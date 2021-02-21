## vecotr 容器结构图
![image](https://github.com/luguifang/notes/blob/main/STL/image/p11.jpg)

## 关键代码分析(详见https://github.com/luguifang/notes/blob/main/STL/source-code/gun-2.91.57-for-win/stl_vector.h)
```c++
template <class T, class Alloc = alloc>
class vector {
public:
  typedef T value_type;
  typedef value_type* iterator;
  typedef value_type& reference;
  typedef size_t size_type;
protected:
  iterator start;
  iterator finish;
  iterator end_of_storage;
public:  
  iterator begin() { return start; }
  iterator end() { return finish; }
  size_type size() const { return size_type(end() - begin()); }
  size_type max_size() const { return size_type(-1) / sizeof(T); }
  size_type capacity() const { return size_type(end_of_storage - begin()); }
  reference operator[](size_type n) { return *(begin() + n); }
  reference front() { return *begin(); }
  reference back() { return *(end() - 1); }
  
  //二倍空间增加代码实现逻辑
   void push_back(const T& x) 
   {
    if (finish != end_of_storage) // 如果空间足够则直接放入元素
    {
      construct(finish, x);
      ++finish;
    }
    else //空间不够 扩充空间
      insert_aux(end(), x);
  }
  
  template <class T, class Alloc>
  void vector<T, Alloc>::insert_aux(iterator position, const T& x) 
  {
    // 此处代码和push_back() 中检测重复，因为该函数也会被其他函数调用到。并不是单独被push_back()调用
    if (finish != end_of_storage)
    {
      construct(finish, *(finish - 1));
      ++finish;
      T x_copy = x;
      copy_backward(position, finish - 2, finish - 1);
      *position = x_copy;
    }
    else //已经没有备用空间
    {
      const size_type old_size = size();
      const size_type len = old_size != 0 ? 2 * old_size : 1;
      iterator new_start = data_allocator::allocate(len);
      iterator new_finish = new_start;
      /* 分配原则： 如果原大小为0 则分配1个空间大小，如果原大小不是0则分配原大小的2倍，前一部分放置原来数据后一部分放置新增数据*/
      __STL_TRY 
      {
        new_finish = uninitialized_copy(start, position, new_start); // 将原容器的内容拷贝到新的容器中
        construct(new_finish, x);
        ++new_finish; // 调整位置
        new_finish = uninitialized_copy(position, finish, new_finish); // 可能是insert 动作调入到该函数，所以还要考虑将按插点后的元素做一次copy
      }

#ifdef  __STL_USE_EXCEPTIONS 
      catch(...) 
      {
        destroy(new_start, new_finish); 
        data_allocator::deallocate(new_start, len);
        throw;
      }
#endif /* __STL_USE_EXCEPTIONS */
    // 释放旧的容器
    destroy(begin(), end());
    deallocate();
    
    // 调整迭代器，指向新的元素
    start = new_start;
    finish = new_finish;
    end_of_storage = new_start + len;
  }
}

  
  
  
  
```

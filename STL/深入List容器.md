# G2.9+ List的实现
## list容器结构图
 ![image](https://github.com/luguifang/notes/blob/main/STL/image/p3.png)
## list 实现细节
  1、G2.9 list 的实现文件为 stl_list.h
  2、实现关键结构字段

```c++
template <class T>
struct __list_node {
  typedef void* void_pointer;
  void_pointer next;
  void_pointer prev;
  T data;
};

template<class T, class Ref, class Ptr>
struct __list_iterator {
  typedef T value_type;
  typedef Ptr pointer;
  typedef Ref reference;
  ...

};


template <class T, class Alloc = alloc>
class list {
protected:
  typedef __list_node<T> list_node;
  link_type node;
  
public:
  typedef list_node* link_type;
  typedef __list_iterator<T, T&, T*>  iterator;

  typedef T value_type;
  typedef value_type* pointer;
  typedef const value_type* const_pointer;
  typedef value_type& reference;
  typedef const value_type& const_reference;
  typedef size_t size_type;
  typedef ptrdiff_t difference_type;
  ...
};
```

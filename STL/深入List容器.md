# G2.9+ List的实现
## list容器结构图
 ![image](https://github.com/luguifang/notes/blob/main/STL/image/p3.png)
## list 实现关键代码及关联结构体关键代码
    1、G2.9 list 的实现文件为 stl_list.h
    2、实现关键结构的源代码:
```c++
template <class T>
struct __list_node {
  typedef void* void_pointer;
  void_pointer next; // 这里的指针类型为void 使用时需要进行转换 ，应该为该数据类型的指针，后续某个版本之后已经做了更改
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
  typedef __list_iterator<T, T&, T*>  iterator; //迭代器

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
## list的迭代器的实现
```c++
template<class T, class Ref, class Ptr>
struct __list_iterator {
  typedef __list_iterator<T, T&, T*>             iterator;    
  typedef __list_iterator<T, const T&, const T*> const_iterator;
  typedef __list_iterator<T, Ref, Ptr>           self;

  typedef bidirectional_iterator_tag iterator_category; //(1)
  typedef T value_type;    //(2)
  typedef Ptr pointer;     //(3)
  typedef Ref reference;   //(4)
  typedef __list_node<T>* link_type;
  typedef size_t size_type;
  typedef ptrdiff_t difference_type; //(5)

  link_type node;

  __list_iterator(link_type x) : node(x) {}
  __list_iterator() {}
  __list_iterator(const iterator& x) : node(x.node) {}

  bool operator==(const self& x) const { return node == x.node; }
  bool operator!=(const self& x) const { return node != x.node; }
  reference operator*() const { return (*node).data; }
  pointer operator->() const { return &(operator*()); }

  /*c++ 规定前置++ (++i)无参数 后置++ (i++)有参数*/
  self& operator++() { 
    node = (link_type)((*node).next);
    return *this;
  }
  /*c++ 规定 后置++ 不能进行2次 比如i++++ 就是错误的 所以这儿的实现返回值没有使用引用的，目的为了禁止两次后置++ 操作*/
  self operator++(int) { 
    self tmp = *this;  // 记录原值，调用拷贝构造函数
    ++*this;           // 进行操作，调用前置++ 完成操作
    return tmp;
  }
  ...

};
```
    (1)(2)(3)(4)(5) 每个容器的iterator 必须有的5个typedef

## G2.9 及G4.9之后版本list的区别
    G4.9 之后iterator 的模板参数只有一个，易于使用
    G4.9 之后node 的结构有其parent,引入了继承，结构变的复杂
    G4.9 之后node 的成员type较为准确，以前使用了void





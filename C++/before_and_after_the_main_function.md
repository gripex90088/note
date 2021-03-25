+ 在main函数之前执行

  ```cpp
  __attribute__((constructor)) void constructor_func()
  {
  	printf("Before main functionn");    
  }
  ```

  

+　在main函数之后

  ```cpp
  __attribute__((destructor)) void destructor_func()
  {
      printf("After main function\n");
  }
  ```

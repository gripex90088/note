### smart_pointer

+ shared_ptr

  ```cpp
  int a = 10;
  shared_ptr<int> sp1 = make_shared<int>(a);
  shared_ptr<int> sp2 = sp1;
  cout << sp2.use_count() << endl;
  ```

+ unique_ptr

  ```cpp
  unique_ptr<int> up1(new int);
  ```

+ 
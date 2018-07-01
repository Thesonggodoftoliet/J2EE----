# J2EE开发实训

//一个本科咸鱼的课余生活

1.java笔试i++(++i）//自增自减

2.finall 需要出现在数据库连接这种即使操作未完成也需要关闭

3.单例模式懒汉或饿汉式
      单例模式：应用该模式的类，一个类只有一个实例。
      懒汉式：在你需要的时候才去创建这个对象
	public class Study{
		private static Study student;	
		private Study(){};//外界不能创建对象，所以将构造方法私有
		public static Study getstudent(){
			if(student == null){
				student = new Study();
			}
			return student;
		}
	}

      饿汉式：不管需不需要，一开始就创建对象
	public class Study{
		private static final Study student = new Study();
		private Study(){};
		public static Study getstudent(){
			return student;
		}
	} 

4.冒泡排序

	void bubble_sort(int a[],int len){
		int t;
		for( int i = 0; i < len - 1; ++i)
			for(int j = 0; j<len-1-i;++j)
				if(a[i] < a[j]){
					t = a[i];
					a[i] = a[j];
					a[j] = t;}
	}
## 向上转型
```
List<Task> taskList = new ArrayList<Task>();   //基类Task的List集合
		Task math = new Homework(1, "Math", "math homework", "2018-09-18", 0, "2018-09-21");
		taskList.add(math);
    
		Task algorithm = new Homework(2, "Algorithm", "algorithm homework", "2018-09-15", 0, "2018-09-18");
		taskList.add(algorithm);
    
    Task computerScience = new Experiment(3, "Computer Science", "computer science experiment", "2018-09-13", 0,
				"2018-09-18", 2);
		taskList.add(computerScience);
    
		Task networkingProgramming = new Experiment(4, "Network Programming", "network programming experiment",
				"2018-09-12", 0, "2018-09-22", 4);
		taskList.add(networkingProgramming);
    
		Task numericalAnalysis = new ClassroomTask(5, "Numerical Analysis", "numerical analysis classroom task",
				"2018-09-6", 0);   //向上转型
				
     
   public void displayCatalogTask() {
    for (Task task : catalogTask) 
			stdOut.println(task.toString());	  //task 实际上为子类 ，调用子类的toString() 避免分类讨论
	}
```
  ### 注意：向上转型为基类对象，调用基类和子类的同名方法用的是子类方法，不能调用子类不同名的方法。要调用子类不同名方法还要再向上转型
 ## 向下转型  
 ```
 FacultyMember类中equals
  public class FacultyMember {
     private String name;
   public  String getName(){return name;}
   
   public boolean equals(Object o){  //o对象  不能直接调用FacultyMember的方法
	   if( o instanceof FacultyMember)  //$ 判断o 是不是FacultyMember类    instanceof
	   { FacultyMember member = (FacultyMember) o;  //$ 向下转型
	   if(this.name.equals(member.getName()))return true;}
	   else return false;
	   }
 ```

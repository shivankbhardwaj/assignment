import java.util.*;

class QueueUsingStacks
{  

	static Stack<Integer> s1=new Stack<Integer>();  
	static Stack<Integer> s2=new Stack<Integer>();  
  
    static void enQueue(int x)  
    {  
        while(!s1.isEmpty()) 
        {  
            s2.push(s1.pop());  
        }  
  
        s1.push(x);  
  
        while(!s2.isEmpty())  
        {  
            s1.push(s2.pop());   
        }  
    }  
  
    static int deQueue()  
    {  
        if(s1.isEmpty())  
        {  
            System.out.println("Queue is empty!");  
            return 0;
        }  
 
        int n=s1.peek();  
        s1.pop();  
        return n;  
    }  
  
public static void main(String[] args)  
{  
    QueueUsingStacks q = new QueueUsingStacks();  
    q.enQueue(1);  
    q.enQueue(2);  
    q.enQueue(3);  
  
    System.out.println(q.deQueue());  
    System.out.println(q.deQueue()); 
    System.out.println(q.deQueue()); 
}  
}
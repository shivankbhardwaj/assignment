import java.util.*;

public class printEvenLevel
{
    static Node root;

    class Node
    {
        int data;
        Node left;
        Node right;

        Node(int data)
        {
            this.data=data;
            left=right=null;
        }
    }

    public Node insert(Node node, int data)
    {
        if(node==null)
        {
            return new Node(data);
        }

        if(data<node.data)
        {
            if(node.left!=null)
            {
                insert(node.left, data);
            }
            else
                node.left=new Node(data);
        }
        else if(data>node.data)
        {
            if(node.right!=null)
            {
                insert(node.right, data);
            }
            else
                node.right=new Node(data);
        }
        return node;
    }

    public void add(int data)
    {
        root=insert(root, data);
    }

    public int height(Node root)
    {
        int lh=0;
        int rh=0;;
        int h=0;

        if(root==null)
        {
            return 0;
        }
        else
        {
            lh=height(root.left);
            rh=height(root.right);

            if(lh>rh)
            {
                return lh+1;
            }
            else
                return rh+1;
        }
    }
	
	public void printOrder()
	{
		int h=height(root);
		for(int i=1;i<=h;i=i+2)
		{
			printLevel(root,i);
		}
	}

	public void printLevel(Node root, int level)
	{
		if(root==null)
		{
			return;
		}
		else if(level==1)
		{
			System.out.println(root.data);
		}
		else if(level>1)
		{
			printLevel(root.right,level-1);
			printLevel(root.left,level-1);
		}
			
	}


    public static void main(String args[])
    {
        printEvenLevel bt = new printEvenLevel();
         
        bt.add(50);
        bt.add(30);
        bt.add(80);
        bt.add(10);
        bt.add(40);
		bt.add(70);
		bt.add(150);
		
		bt.printOrder();
    }
}
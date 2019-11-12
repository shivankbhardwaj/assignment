import java.util.*;

public class heightTree
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

    public void displayinOrder(Node node)
    {
        if(node!=null)
        {
            displayinOrder(node.left);
            System.out.print(" "+node.data);
            displayinOrder(node.right);
        }
    }

    public int height(Node node)
    {
        int lh=0;
        int rh=0;;
        int h=0;

        if(node.left!=null)
        {
            lh=height(node.left);
        }
        else if(node.right!=null)
        {
            rh=height(node.right);
        }

        if(lh>rh)
        {
            h=lh;
        }
        else    
            h=rh;

        return h+1;
    }

    public static void main(String args[])
    {
        heightTree bt = new heightTree();
         
        bt.add(1);
        bt.add(2);
        bt.add(3);
        bt.add(4);
        bt.add(5);
        bt.displayinOrder(root);

        System.out.println("Height of tree: "+bt.height(root));
    }
}
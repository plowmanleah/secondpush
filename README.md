# secondpush
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package trie;
import java.io.*;
import java.util.*;
/**
 *
 * @author plowmanleah
 */
class TrieNode {
    private Node root;
    private Node child;
    private Node sibling;
    public File file;
    public String newWord;
    
    public TrieNode()
    {
        root = new Node();
        child = null;
        sibling = null;
    }
    
    public void begTrie(String word)
    {
        if(child != null)
        {
            return;
        }
        
        Node currentNode = root;
        for(int i = 0; i < word.length();i++)
        {
            char letter = word.charAt(0);
            int index = letter - 'a';
            String aWord = word.substring(0, i+1);
            currentNode.curNode[index] = new Node(aWord);
        }
        currentNode.corWord = true;
        child = currentNode;
    }
    
    public void addWord() throws FileNotFoundException
    {
        Node currentNode = root;
        file = new File("dictionary.txt");
        Scanner scan = new Scanner(file);
        while(scan.hasNext())
        {
            newWord = scan.next();
            System.out.println(newWord);
            if(child == null)
            {
                begTrie(newWord);
                System.out.println("in child");
                return;
            }
            Node next = null;
            Node previous = null;
            System.out.println("after child");
            for(int i = 0; i < newWord.length(); i++)
            {
                char letter = newWord.charAt(i);
                int index = letter - 'a';
                if(currentNode.curNode[index] != null)
                {
                    currentNode = currentNode.curNode[index];
                    System.out.println(currentNode);
                }
            }
            System.out.println(currentNode);
        }
    }
    
    public Node findNext(Node aNode, int wordIndex)
    {
        if(aNode == null)
        {
            return null;
        }
        String nullWord = aNode.toString();
        for(int i = wordIndex; i < aNode.curNode.length; i++)
        {
            
        }
        return aNode;
    }
    public void inputFile() throws FileNotFoundException
    {
        file = new File("dictionary.txt");
        Scanner scan = new Scanner(file);
        while(scan.hasNext()){
            newWord = scan.next();
            System.out.println(newWord);
        }
    }
    
}


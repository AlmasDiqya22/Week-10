# Week-10
Tugas Artificial Intelligent and Aplication Week 10
Nama		: Almas Diqya Wafa’
NIM		: 5311421005
Prodi		: Teknik Elektro
Mata Kuliah	            : Artificial Intellegent and Aplication
Rombel	            : Senin 09.00

MODUL 4
“Teknik Pencarian Blind Search”

1.	Tentukan bagaimana algoritma BFS di atas dapat menentukan node ke 8, 6, dan 7.
   
Program:
import java.util.ArrayDeque; 
import java.util.ArrayList; 
import java.util.HashMap; 
import java.util.List; 
import java.util.Map; 
import java.util.Queue; 
import java.util.Set; 

public class AdjacencyList 
{ 
public enum NodeColour { WHITE, GRAY, BLACK } 
public static class Node 
{ 
int data; 
int distance; 
NodeColour colour; 
public Node(int data) 
{ 
            this.data = data; 
        }  
    /**
     *
     * @return
     */
    @Override
        public String toString() 
        { 
         return "(" + data + ",d=" + distance + ")"; 
        } 
    } 
    Map<Node, List<Node>> nodes; 
    public AdjacencyList() 
    { 
        nodes = new HashMap<>(); 
    } 
    public void addEdge(Node n1, Node n2) 
    { 
        if (nodes.containsKey(n1)) { 
            nodes.get(n1).add(n2); 
        } else { 
       ArrayList<Node> list = new ArrayList<>(); 
            list.add(n2); 
            nodes.put(n1, list); 
        } 
    } 
    public void bfs(Node s) 
    { 
        Set<Node> keys = nodes.keySet(); 
        for (Node u : keys) { 
            if (u != s) { 
                u.colour = NodeColour.WHITE; 
                u.distance = Integer.MAX_VALUE; 
            } 
        } 
        s.colour = NodeColour.GRAY; 
        s.distance = 0; 
        Queue<Node> q = new ArrayDeque<>(); 
        q.add(s); 
        while (!q.isEmpty()) { 
            Node u = q.remove(); 
            List<Node> adj_u = nodes.get(u); 
            if (adj_u != null) { 
                for (Node v : adj_u) { 
                    if(v.colour == NodeColour.WHITE) { 
                        v.colour = NodeColour.GRAY; 
                        v.distance = u.distance + 1; 
                        q.add(v); 
                    } 
                } 
            } 
            u.colour = NodeColour.BLACK; 
            System.out.print(u + " "); 
        } 
    } 
    public static void main(String[] args)
     { 
        AdjacencyList graph = new AdjacencyList(); 
        Node n1 = new Node(1); 
        Node n2 = new Node(2); 
        Node n3 = new Node(3); 
        Node n4 = new Node(4); 
        Node n5 = new Node(5); 
        Node n6 = new Node(6); 
        Node n7 = new Node(7); 
        Node n8 = new Node(8); 
        graph.addEdge(n1, n2);   
        graph.addEdge(n2, n1); 
        graph.addEdge(n2, n3);   
        graph.addEdge(n3, n4); 
        graph.addEdge(n3, n2);   
        graph.addEdge(n4, n3); 
        graph.addEdge(n4, n5); 
        graph.addEdge(n4, n6);  
        graph.addEdge(n5, n4); 
        graph.addEdge(n5, n6); 
        graph.addEdge(n5, n7); 
        graph.addEdge(n6, n4); 
        graph.addEdge(n6, n5); 
        graph.addEdge(n6, n7); 
        graph.addEdge(n6, n8); 
        graph.addEdge(n7, n5); 
        graph.addEdge(n7, n6); 
        graph.addEdge(n7, n8); 
        graph.addEdge(n8, n6); 
        graph.addEdge(n8, n7); 
        graph.bfs(n3); 
    } 
}

Hasil:
Setelah melakukan praktikum menggunakan software Netbeans dan melakukan uji coba pada Modul 4 (nomo1) ditemukan hasil sebagai berikut.
(3,d=0) (4,d=1) (2,d=1) (5,d=2) (6,d=2) (1,d=2) (7,d=3) (8,d=3) BUILD SUCCESSFUL (total time: 0 seconds)

Penjelasan:
Algoritma Breadth-First Search (BFS) digunakan untuk mencari jalur terpendek dari satu simpul (node) ke simpul lain dalam graf. Dalam program di atas, BFS dimulai dari simpul (node) ke-3 (n3). Berikut langkah-langkah untuk mencapai node ke-8, 6, dan 7:

1. *Node 3 (d=0):* BFS dimulai dari simpul n3 dengan jarak 0.
2. *Node 4 (d=1):* n3 memiliki tetangga n4, sehingga BFS melanjutkan ke n4 dengan jarak 1.
3. *Node 2 (d=1):* n4 memiliki tetangga n2, tetapi n2 sudah diwarnai GRAY (dalam proses BFS), jadi BFS tidak melanjutkan ke n2.
4. *Node 5 (d=2):* n4 juga memiliki tetangga n5, yang belum diwarnai, jadi BFS melanjutkan ke n5 dengan jarak 2.
5. *Node 6 (d=2):* n5 memiliki tetangga n6, yang belum diwarnai, jadi BFS melanjutkan ke n6 dengan jarak 2.
6. *Node 1 (d=2):* n5 juga memiliki tetangga n1, yang belum diwarnai, jadi BFS melanjutkan ke n1 dengan jarak 2.
7. *Node 7 (d=3):* n6 memiliki tetangga n7, yang belum diwarnai, jadi BFS melanjutkan ke n7 dengan jarak 3.
8. *Node 8 (d=3):* n6 juga memiliki tetangga n8, yang belum diwarnai, jadi BFS melanjutkan ke n8 dengan jarak 3.

Dengan demikian, algoritma BFS pada graf di atas ditemukan node ke-8, 6, dan 7 dengan jarak masing-masing 3 dari node awal (n3).



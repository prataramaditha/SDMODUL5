# CODELAB 1
# Program Traversal BinaryTree

## Gambaran Umum

Program Java ini mendemonstrasikan implementasi pohon biner (binary tree) beserta tiga metode traversing atau penjelajahan pohon: In-order, Pre-order, dan Post-order. Struktur pohon dibangun secara manual dalam metode utama, dan hasil traversing ditampilkan di konsol.

## Struktur Program

Program ini terdiri dari dua kelas utama:
1. `Node`: Mewakili sebuah node dalam pohon biner.
2. `BinaryTree`: Mengelola pohon biner dan mengimplementasikan metode traversing.

### Kelas Node

```java
class Node {
    int data;
    Node left;
    Node right;

    public Node(int data) {
        this.data = data;
    }
}
```

### Kelas BinaryTree

```java
class BinaryTree {
    public Node root;

    public BinaryTree() {
        root = null;
    }

    public void addRoot(int data) {
        root = new Node(data);
    }

    public void inOrder(Node node) {
        if (node != null) {
            inOrder(node.left);
            System.out.println(node.data + " ");
            inOrder(node.right);
        }
    }

    public void preOrder(Node node) {
        if (node != null) {
            System.out.println(node.data + " ");
            preOrder(node.left);
            preOrder(node.right);
        }
    }

    public void postOrder(Node node) {
        if (node != null) {
            postOrder(node.left);
            postOrder(node.right);
            System.out.println(node.data + " ");
        }
    }
}
```

### Metode Main

```java
public static void main(String[] args) {
    BinaryTree tree = new BinaryTree();

    // Menentukan struktur pohon secara manual
    tree.addRoot(20);
    tree.root.left = new Node(2);
    tree.root.right = new Node(25);
    tree.root.left.left = new Node(37);
    tree.root.left.right = new Node(12);
    tree.root.right.right = new Node(16);

    System.out.println("\nPre Order: ");
    tree.preOrder(tree.root);
    System.out.println("\nIn Order: ");
    tree.inOrder(tree.root);
    System.out.println("\nPost Order: ");
    tree.postOrder(tree.root);
}
```

## Struktur Pohon

Pohon yang dibangun dalam metode `main` memiliki struktur sebagai berikut:

```
        20
       /  \
      2    25
     / \     \
    37  12    16
```

## Metode Traversal

- **In-order Traversal (Kiri, Akar, Kanan)**: Mengunjungi node dengan urutan berikut: 37, 2, 12, 20, 25, 16.
- **Pre-order Traversal (Akar, Kiri, Kanan)**: Mengunjungi node dengan urutan berikut: 20, 2, 37, 12, 25, 16.
- **Post-order Traversal (Kiri, Kanan, Akar)**: Mengunjungi node dengan urutan berikut: 37, 12, 2, 16, 25, 20.

## Cara Menjalankan

1. Kompilasi program menggunakan Java compiler:
   ```sh
   javac Codelab/BinaryTree.java
   ```
2. Jalankan program Java yang sudah dikompilasi:
   ```sh
   java Codelab.BinaryTree
   ```

## Output

Program akan mencetak hasil traversal dari pohon biner ke konsol:

```
Pre Order: 
20 
2 
37 
12 
25 
16 

In Order: 
37 
2 
12 
20 
25 
16 

Post Order: 
37 
12 
2 
16 
25 
20 
```

## Ringkasan

Program ini memberikan contoh sederhana tentang cara membuat pohon biner dan melakukan berbagai jenis traversal pohon. Kelas `BinaryTree` berisi metode untuk menambahkan akar dan melakukan traversal pohon dalam berbagai urutan. Output menunjukkan urutan node yang dikunjungi selama masing-masing traversal.

# CODELAB 2
# Program Traversal BinaryTree2

## Gambaran Umum

Program Java ini mendemonstrasikan implementasi pohon biner (binary tree) beserta tiga metode traversing atau penjelajahan pohon: In-order, Pre-order, dan Post-order. Struktur pohon dibangun secara dinamis melalui metode `NewNode`, dan hasil traversing ditampilkan di konsol.

## Struktur Program

Program ini terdiri dari dua kelas utama:
1. `Node2`: Mewakili sebuah node dalam pohon biner.
2. `BinaryTree2`: Mengelola pohon biner dan mengimplementasikan metode traversing.

### Kelas Node2

```java
class Node2 {
    int data;
    Node2 left;
    Node2 right;

    public Node2(int data) {
        this.data = data;
    }
}
```

### Kelas BinaryTree2

```java
class BinaryTree2 {
    public Node2 root;

    public void NewNode(int data) {
        root = NewNode(root, new Node2(data));
    }

    private Node2 NewNode(Node2 root, Node2 newData) {
        if (root == null) {
            root = newData;
            return root;
        }

        if (newData.data < root.data) {
            root.left = NewNode(root.left, newData);
        } else {
            root.right = NewNode(root.right, newData);
        }

        return root;
    }

    public void inOrder(Node2 node) {
        if (node != null) {
            inOrder(node.left);
            System.out.println(node.data + " ");
            inOrder(node.right);
        }
    }

    public void preOrder(Node2 node) {
        if (node != null) {
            System.out.println(node.data + " ");
            preOrder(node.left);
            preOrder(node.right);
        }
    }

    public void postOrder(Node2 node) {
        if (node != null) {
            postOrder(node.left);
            postOrder(node.right);
            System.out.println(node.data + " ");
        }
    }
}
```

### Metode Main

```java
public static void main(String[] args) {
    BinaryTree2 tree = new BinaryTree2();

    tree.NewNode(20);
    tree.NewNode(2);
    tree.NewNode(25);
    tree.NewNode(37);
    tree.NewNode(16);

    System.out.println("\nPre Order: ");
    tree.preOrder(tree.root);
    System.out.println("\nIn Order: ");
    tree.inOrder(tree.root);
    System.out.println("\nPost Order: ");
    tree.postOrder(tree.root);
}
```

## Struktur Pohon

Pohon yang dibangun menggunakan metode `NewNode` memiliki struktur sebagai berikut:

```
        20
       /  \
      2    25
             \
              37
             /
            16
```

## Metode Traversal

- **In-order Traversal (Kiri, Akar, Kanan)**: Mengunjungi node dengan urutan berikut: 2, 16, 20, 25, 37.
- **Pre-order Traversal (Akar, Kiri, Kanan)**: Mengunjungi node dengan urutan berikut: 20, 2, 25, 16, 37.
- **Post-order Traversal (Kiri, Kanan, Akar)**: Mengunjungi node dengan urutan berikut: 16, 2, 37, 25, 20.

## Cara Menjalankan

1. Kompilasi program menggunakan Java compiler:
   ```sh
   javac Codelab/BinaryTree2.java
   ```
2. Jalankan program Java yang sudah dikompilasi:
   ```sh
   java Codelab.BinaryTree2
   ```

## Output

Program akan mencetak hasil traversal dari pohon biner ke konsol:

```
Pre Order: 
20 
2 
25 
16 
37 

In Order: 
2 
16 
20 
25 
37 

Post Order: 
16 
2 
37 
25 
20 
```

## Ringkasan

Program ini memberikan contoh sederhana tentang cara membuat pohon biner secara dinamis dan melakukan berbagai jenis traversal pohon. Kelas `BinaryTree2` berisi metode untuk menambahkan node baru dan melakukan traversal pohon dalam berbagai urutan. Output menunjukkan urutan node yang dikunjungi selama masing-masing traversal.

# AVL 트리

트리 내의 어떤 노드도 좌서브 트리와 우서브 트리의 높이 차가 1보다 크지 않은 상태로 유지되는 이진 검색 트리

### Left Rotate

```java

    private AVLNode leftRotate(AVLNode tNode) {

        AVLNode RChild = tNode.right;
        AVLNode RLChild = RChild.left;

        tNode.right = RChild.right;
        RChild.left = tNode;
        tNode.right = RLChild;

        return RChild;
    }

```

### Right Rotate

``` java

    private AVLNode rightRotate(AVLNode tNode) {

        AVLNode LChild = tNode.left;
        AVLNode LRChild = LChild.right;

        LChild.right = tNode;
        tNode.left = LRChild;

        return LChild;
    }


```

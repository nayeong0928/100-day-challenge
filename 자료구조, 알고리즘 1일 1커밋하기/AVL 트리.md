# AVL 트리

- 트리 내의 어떤 노드도 좌서브 트리와 우서브 트리의 높이 차가 1보다 크지 않은 상태로 유지되는 이진 검색 트리
- 균형이 깨지면 가장 낮은 서브트리부터 수선

### 서브 트리
- LL트리: 중심노드의 왼자식의 좌서브트리
- LR트리: 중심노드의 왼자식의 우서브트리
- RR트리: 중심노드의 오른쪽 자식의 우서브트리
- RL트리: 중심노드의 오른쪽 자식의 좌서브트리

### 타입
t: 중심노드
|타입|가장 깊은 트리|해결방법|
|------|---|---|
|LL타입|t.left.left|t 우회전|
|LR타입|t.left.right|t.left 좌회전 -> t 우회전|
|RR타입|t.right.right|t 좌회전|
|RL타입|t.right.left|t.right 우회전 -> t 좌회전|


```java


    private AVLNode leftRotate(AVLNode t) {
        AVLNode RChild = t.right;

        if (RChild == NIL) {
            System.out.println(t.item + "'s RChild shouldn't be NIL!!!");
        }
        AVLNode RLChild = RChild.left;
        RChild.left = t;
        t.right = RLChild;
        t.height = 1 + Math.max(t.left.height, t.right.height);
        RChild.height = 1 + Math.max(RChild.left.height, RChild.right.height);
        return RChild;
    }

    private AVLNode rightRotate(AVLNode t) {
        AVLNode LChild = t.left;

        if (LChild == NIL) {
            System.out.println(t.item + "'s item LChild shouln't be NIL!!!");
        }
        AVLNode LRChild = LChild.right;
        LChild.right = t;
        t.left = LRChild;
        t.height = 1 + Math.max(t.left.height, t.right.height);
        LChild.height = 1 + Math.max(LChild.left.height, LChild.right.height);
        return LChild;
    }


```

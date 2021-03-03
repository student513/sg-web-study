1. Sorting solution

   - Sorting 알고리즘에서 stable의 의미는?
     동일한 엘리멘트가 있을 때 정렬 전후의 순서가 같다

   - Sorting 알고리즘의 가짓 수가 많은 이유는?
     정렬 속도가 다 다르다.
     속도가 아닌 공간 복잡도가 이슈일 수 있다.

2. Bubble sort, Selection sort, Insertion Sort

   - Time complexity: O(n^2)

3. Merge sort

   - 분할정복으로 나눠지지 않을 때까지 나눈 다음, 대소비교를 하여 merge시킨다
   - O(nlogn)

4. Heap sort

   - 힙에 데이터를 삽입하여 루트노드의 값을 차례대로 정렬하는 것
   - O(nlogn)

5. Quick sort가 무엇인가?
   - divide and conquer를 이용해 정렬을 수행하는 알고리즘. partitioning이라는 아이디어를 사용한다
   - 피벗 엘리먼트를 기준으로 좌우로 크기에 따라 나눈다.
   - O(nlogn)
     최악의 경우 O(n^2): 피벗 값이 항상 가장 작거나 가장 클 경우

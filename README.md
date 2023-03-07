# quick_sort<br>
Java 퀵 정
렬<br>
## 퀵 정렬(quick sort) 알고리즘의 개념 요약<br>
‘찰스 앤터니 리처드 호어(Charles Antony Richard Hoare)’가 개발한 정렬 알고리즘<br>
퀵 정렬은 불안정 정렬 에 속하며, 다른 원소와의 비교만으로 정렬을 수행하는 비교 정렬 에 속한다.<br>
분할 정복 알고리즘의 하나로, 평균적으로 매우 빠른 수행 속도를 자랑하는 정렬 방법<br>
합병 정렬(merge sort)과 달리 퀵 정렬은 리스트를 비균등하게 분할한다.<br>
### 분할 정복(divide and conquer) 방법<br>
문제를 작은 2개의 문제로 분리하고 각각을 해결한 다음, 결과를 모아서 원래의 문제를 해결하는 전략이다.<br>
분할 정복 방법은 대개 순환 호출을 이용하여 구현한다.<br>
## 장점과 단점<br>
### 장점<br>
속도가 빠르다<br>
시간 복잡도가 O(nlogn)을 가지는 다른 정렬 알고리즘과 비교했을 때도 가장 빠르다.<br>
추가 메모리 공간을 필요로 하지 않는다.<br>
퀵정렬은 O(logn)만큼의 메모리를 필요로 한다.<br>
### 단점<br>
-정렬된 리스트에 대해서는 퀵정렬의 불균형 분할에 의해 오히려 수행시간이 더 많이 걸린다.<br>
퀵정렬의 불균형 분할을 방지하기 위하여 피벗을 선택할 때 더욱 리스트를 균등하게 분할할 수 있는 데이터를 선택한다.<br>
(예를들어 리스트내의 몇개의데이터 중에서 크기순으로 중간 값을 피벗으로 선택한다.)<br>
## 예시<br>
![image](https://user-images.githubusercontent.com/126844692/223330345-61c12e84-15a3-48fa-ad1b-6f59b7b8fca9.png)
## 설명<br>
피벗 값을 입력 리스트의 첫 번째 데이터로 하자. (다른 임의의 값이어도 상관없다.)<br>
2개의 인덱스 변수(low, high)를 이용해서 리스트를 두 개의 부분 리스트로 나눈다.<br>
### 1회전<br>
피벗이 5인 경우, low는 왼쪽에서 오른쪽으로 탐색해가다가 피벗보다 큰 데이터(8)을 찾으면 멈춘다.<br>
high는 오른쪽에서 왼쪽으로 탐색해가다가 피벗보다 작은 데이터(2)를 찾으면 멈춘다.<br>
low와 high가 가리키는 두 데이터를 서로 교환한다.<br>
이 탐색-교환 과정은 low와 high가 엇갈릴 때까지 반복한다.<br>
### 2회전<br>
피벗(1회전의 왼쪽 부분리스트의 첫 번째 데이터)이 1인 경우,<br>
위와 동일한 방법으로 반복한다.<br>
### 3회전<br>
피벗(1회전의 오른쪽 부분리스트의 첫 번째 데이터)이 9인 경우,<br>
위와 동일한 방법으로 반복한다.<br>
## for문<br>

package 자바;<br>
import java.util.*;<br>
public class quick_sort {<br>
	

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Integer[] array = {5, 7, 3, 1, 3};
        ArrayList<Integer> list = new ArrayList<Integer>(Arrays.asList(array));
        split(list);
    }

    private static void split(ArrayList<Integer> list) {
        if(list.size() <= 1){
            return;
        }

        int pivot = list.get(0);
        ArrayList<Integer> leftArray = new ArrayList<Integer>();
        ArrayList<Integer> rightArray = new ArrayList<Integer>();

        for(int i = 1; i < list.size(); i++){
            if(list.get(i) > pivot){
                rightArray.add(list.get(i));
            }else {
                leftArray.add(list.get(i));
            }
        }

        ArrayList<Integer> mergedArray = new ArrayList<Integer>();
        mergedArray.addAll(leftArray);
        mergedArray.addAll(Arrays.asList(pivot));
        mergedArray.addAll(rightArray);

        System.out.println(mergedArray);
	}
}

## 출력 결과<br>
[3, 1, 3, 5, 7]<br>
## 실행된 이미지<br>
![image](https://user-images.githubusercontent.com/126844692/223335013-f3439c85-cd87-4204-bfbc-60f357b44454.png)

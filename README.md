# MAOPAO-
单元测试
## 1.让我们对自己的代码有信心
修改了代码后单测依然通过的，起码说明我们的修改没有破坏程序的正确性。这从主观上能增加我们对代码的信心。虽然单元测试通过了并不意味着程序就没有bug了，但我们也要了解到这可能不是单元测试的问题。单元测试顾名思义是测试一个”单元”，这个”单元”一般是类或方法，而不是整个系统。对整个系统的测试那是集成测试，功能测试的职责。单元测试追求的是快速反馈，频繁执行。集成测试虽然测“全局”，但成本较高，所以执行频率较少。两者使用场景不同，目的不同。
## 2.为代码重构保驾护航
看到代码很差劲，想重构，但又担心重构之后出问题，怎么办呢？如果有单元测试情况就不一样了，重构完代码，跑一遍单元测试，如果单元测试都通过，基本上可以保证我们的重构没有破坏原来代码逻辑的正确性。不过前提是之前的写的单元测试质量很好，覆盖率很高。当然这仅限于小范围的重构，比如重构一个类或者函数的实现，但对于大刀阔斧的重构（比如单体重构成微服务，面向库表模式重构成DDD），就不适用，那个时候要重写单元测试了。
## 3.通过单元测试快速熟悉代码
单元测试不仅起到了测试的作用，还是一种很好的“文档”，通过单元测试，我们不需要深入的阅读代码，便能知道这段代码做什么工作，有哪些特殊情况需要考虑，包含哪些业务。

## 代码
package 测试Test;

public class test_1 {
	public static void main(String[] args) {
		int[] chengji = {-1, -15, -5586, 5956,10,15,48,85,6,21,35,48,58,16,25};
     	printArr(chengji);
		bubbleArray(chengji);
		System.out.println();
		printArr(chengji);
//		System.out.print(chengji);
	}
		private static void printArr(int[] chengji) {
			for(int i = 0 ; i< chengji.length ; i++) {
				 System.out.print(chengji[i]+ " ");
			}
		}
	
	
	public static String printArray(int[] chengji) {
		String s = "";
		for(int i = 0 ; i< chengji.length ; i++) {
			 String.join(s, chengji[i]+ " ");
		}
		return s ;
	}
	
	public static void bubbleArray(int chengji[]) {
		for(int i = 0; i<chengji.length-1 ;i++) {
			for(int j = 0;j<chengji.length - i -1 ;j++) {
				if(chengji[j]>chengji[j+1]) {
					int temp = chengji[j];
					chengji[j] = chengji[j+1];
					chengji[j+1] = temp ;
				}
			}
		}
	}
}


package 测试Test;

import static org.junit.Assert.*;

import org.junit.Test;

public class test_1Test {

	@Test
	public void testBubbleArray1() {
		int[] arr1 = {10,95,89,84,26,88,96,75};
		int[] arrend = {25,26,78,84,95,96,99,100};
		test_1.bubbleArray(arr1);
		test_1.printArray(arr1);
		assertTrue(test_1.printArray(arr1).equals(test_1.printArray(arrend)));
				
	}

	@Test
	public void testBubbleArray2() {
		int[] arr2 = {100,95,99,15,43,35,48,78,96,25};
		int[] arrend = {15, 25, 35 ,43 ,48, 78, 95, 96, 99, 100};
		test_1.bubbleArray(arr2);
		test_1.printArray(arr2);
		assertTrue(test_1.printArray(arr2).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray3() {
		int[] arr3 = {100,95,25};
		int[] arrend = {25,95,100};
		test_1.bubbleArray(arr3);
		test_1.printArray(arr3);
		assertTrue(test_1.printArray(arr3).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray4() {
		int[] arr4 = {80,95,95,95,96,96,25};
		int[] arrend = {25 ,95 ,95, 95, 96, 96,80};
		test_1.bubbleArray(arr4);
		test_1.printArray(arr4);
		assertTrue(test_1.printArray(arr4).equals(test_1.printArray(arrend)));
		
	}

	@Test
	public void testBubbleArray5() {
		int[] arr5 = {-1, -15, -5800, 5556,100,95,99,84,26,48,88,6,21,35,48,78,96,25};
		int[] arrend = {-5556, -15 ,-1 ,6 ,21 ,25 ,26 ,35 ,48 ,48, 78 ,84 ,85 ,95 ,96 ,99 ,100 ,5800};
		test_1.bubbleArray(arr5);
		test_1.printArray(arr5);
		assertTrue(test_1.printArray(arr5).equals(test_1.printArray(arrend)));
		
	}

	

}


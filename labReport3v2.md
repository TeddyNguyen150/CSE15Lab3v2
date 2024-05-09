lab3

Pt 1.

Code that needs testing
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Failure inducing input
```
  @Test
  public void testReversed() {
    int[] input1 = { 1, 2, 3 };
    assertArrayEquals(new int[]{ 3, 2, 1 }, ArrayExamples.reversed(input1));
  }
```

Non-failure inducing input
```
  @Test
  public void testReversedEmpty() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```

Output
![image](https://github.com/TeddyNguyen150/CSE15Lab3v2/assets/156158048/c6fa7939-0901-4e28-b154-8bbd68c57de8)

Before
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

After
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

The problem was that the function was setting the input array's values as the empty array's values.
So switching the variables around fixes the bugs.

Pt 2.
Grep:
-o: It gives us the file and what word was found. This is useful because it removes most of the clutter
that comes with grep
```
$ grep -o "testify" 911report/*.txt
911report/chapter-13.1.txt:testify
911report/chapter-13.1.txt:testify
911report/chapter-2.txt:testify
```
```
$ grep -o "estify" 911report/*.txt
911report/chapter-13.1.txt:estify
911report/chapter-13.1.txt:estify
911report/chapter-2.txt:estify
```

-c: Counts how many lines contains the matching word. This is useful to know if a certain word
is used more than others.
```
grep -c "testify" 911report/*.txt
911report/chapter-1.txt:0
911report/chapter-10.txt:0
911report/chapter-11.txt:0
911report/chapter-12.txt:0
911report/chapter-13.1.txt:2
911report/chapter-13.2.txt:0
911report/chapter-13.3.txt:0
911report/chapter-13.4.txt:0
911report/chapter-13.5.txt:0
911report/chapter-2.txt:1
911report/chapter-3.txt:0
911report/chapter-5.txt:0
911report/chapter-6.txt:0
911report/chapter-7.txt:0
911report/chapter-8.txt:0
911report/chapter-9.txt:0
911report/preface.txt:0
```
```
$ grep -c "test" 911report/*.txt
911report/chapter-1.txt:11
911report/chapter-10.txt:0
911report/chapter-11.txt:6
911report/chapter-12.txt:7
911report/chapter-13.1.txt:5
911report/chapter-13.2.txt:13
911report/chapter-13.3.txt:46
911report/chapter-13.4.txt:31
911report/chapter-13.5.txt:47
911report/chapter-2.txt:4
911report/chapter-3.txt:16
911report/chapter-5.txt:5
911report/chapter-6.txt:7
911report/chapter-7.txt:4
911report/chapter-8.txt:2
911report/chapter-9.txt:5
911report/preface.txt:3
```

-n: A prefix that gives us the line where the matching word is found. Useful to find certain sentences.
```
grep -n "test" 911report/*.txt
911report/chapter-1.txt:166:... too long to copy
```
```
grep -n "testify" 911report/*.txt
911report/chapter-13.1.txt:248:                confirmed by the Senate and he or she should testify to the Congress, as is the case
911report/chapter-13.1.txt:535:                President. This official, who would be confirmed by the Senate and would testify
911report/chapter-2.txt:642:                informant for the United States. Also testifying about al Qaeda in a U.S. court was
```

-i: Makes the searched word non-case sensitive. Certain words like I need to be found this way.
```
$ grep "I" 911report/*.txt | wc -l
5046
```
```
$ grep -i "I" 911report/*.txt | wc -l
22772
```

The commands above were found using $ man grep

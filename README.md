# Java Snippets

[![Build status](https://travis-ci.org/iluwatar/java-snippets.svg?branch=master)](https://travis-ci.org/iluwatar/java-snippets)

Inspired by [30 seconds of code](https://github.com/Chalarangelo/30-seconds-of-code), this is a collection of reusable tested Java code snippets.

## How to contribute
Update the sample application with the snippet and add a test for it. After proving that it works update this README.md.

## Table of Contents

### Array
* [Generic two array concatenation](#generic-two-array-concatenation)
* [Generic N array concatenation](#generic-N-array-concatenation)

### File
* [List directories](#list-directories)
* [Read lines from file to string list](#read-lines-from-file-to-string-list)

### Math
* [Factorial](#factorial)
* [Fibonacci](#fibonacci)

### Media
* [Capture screen](#capture-screen)

### String
* [Palindrome check](#palindrome-check)
* [Reverse string](#reverse-string)
* [String to date](#string-to-date)

## Array

### Generic two array concatenation

```java
    public static <T> T[] arrayConcat(T[] first, T[] second) {
        T[] result = Arrays.copyOf(first, first.length + second.length);
        System.arraycopy(second, 0, result, first.length, second.length);
        return result;
    }
```

[⬆ back to top](#table-of-contents)

### Generic N array concatenation

```java
    public static <T> T[] nArrayConcat(T[] first, T[]... rest) {
        int totalLength = first.length;
        for (T[] array : rest) {
            totalLength += array.length;
        }
        T[] result = Arrays.copyOf(first, totalLength);
        int offset = first.length;
        for (T[] array : rest) {
            System.arraycopy(array, 0, result, offset, array.length);
            offset += array.length;
        }
        return result;
    }
```

[⬆ back to top](#table-of-contents)

## File

### List directories

```java
    public static File[] listDirectories(String path) {
        return new File(path).listFiles(File::isDirectory);
    }
```

[⬆ back to top](#table-of-contents)

### Read lines from file to string list

```java
    public static List<String> readLines(String filename) throws IOException {
        return Files.readAllLines(new File(filename).toPath());
    }
```

[⬆ back to top](#table-of-contents)

## Math

### Fibonacci

```java
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        else return fibonacci(n-1) + fibonacci(n-2);
    }
```

[⬆ back to top](#table-of-contents)

### Factorial

```java
    public static int factorial(int number) {
        int result = 1;
        for (int factor = 2; factor <= number; factor++) {
            result *= factor;
        }
        return result;
    }
```

[⬆ back to top](#table-of-contents)

## Media

### Capture screen

```java
    public static void captureScreen(String filename) throws AWTException, IOException {
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        Rectangle screenRectangle = new Rectangle(screenSize);
        Robot robot = new Robot();
        BufferedImage image = robot.createScreenCapture(screenRectangle);
        ImageIO.write(image, "png", new File(filename));
    }
```

[⬆ back to top](#table-of-contents)

## String

### Palindrome check

```java
    public static boolean isPalindrome(String s) {
        StringBuilder sb = new StringBuilder();
        for (char c : s.toCharArray()) {
            if (Character.isLetter(c)) {
                sb.append(c);
            }
        }
        String forward = sb.toString().toLowerCase();
        String backward = sb.reverse().toString().toLowerCase();
        return forward.equals(backward);
    }
```

[⬆ back to top](#table-of-contents)

### Reverse string

```java
    public static String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    }
```

[⬆ back to top](#table-of-contents)

### String to date

```java
    public static Date stringToDate(String date, String format) throws ParseException {
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat(format);
        return simpleDateFormat.parse(date);
    }
```

[⬆ back to top](#table-of-contents)

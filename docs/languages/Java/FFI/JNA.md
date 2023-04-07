# JNA

## 링크

- [JNA Getting Started](https://github.com/java-native-access/jna/blob/master/www/GettingStarted.md)
- [JNA Tutorial - TechBeamersr](https://techbeamers.com/write-a-simple-jna-program-in-java/)
- [Java JNA Example](https://mvallim.github.io/java-jna-example/)

## 기본 예제

### 인터페이스

```java
package test.security;

import com.sun.jna.Library;
import com.sun.jna.Native;
import com.sun.jna.Platform;

public interface nSaferJNAInterface extends Library {

  nSaferJNAInterface INSTANCE = Native.load(
    (Platform.isWindows() ? "msvcrt" : "c"), nSaferJNAInterface.class);

  void printf(String format, Object... args);

  int sprintf(byte[] buffer, String format, Object... args);

  int scanf(String format, Object... args);

  int fflush(Pointer stream);
}
```

### 테스트 코드

```java
{
  nSaferJNAInterface jnaLib = nSaferJNAInterface.INSTANCE;
  jnaLib.printf("Hello World");
  jnaLib.fflush(null);
  String testName = null;

  for (int i = 0; i < 10; i++) {
    jnaLib.printf("\nArgument %d : %s", i, "test");
    jnaLib.fflush(null);
  }

  jnaLib.printf("Please Enter Your Name:\n");
  jnaLib.scanf("%s", testName);
  jnaLib.printf("\nYour name is %s", testName);
}
```

## dll 파일 테스트 - MessageBox

### 인터페이스

```java
package test.security;

import com.sun.jna.Library;
import com.sun.jna.Native;
import com.sun.jna.WString;

public interface nSaferJNAInterface extends Library {

  nSaferJNAInterface INSTANCE = Native.load(
    "C:\\WINDOWS\\system32\\user32.dll", nSaferJNAInterface.class);

  int MessageBoxW(int hWnd, WString lpText, WString lpCaption, int uType);
}
```

### 테스트 코드

```java
{
  nSaferJNAInterface jnaLib = nSaferJNAInterface.INSTANCE;

  jnaLib.MessageBoxW(0,
    new WString("MessageBox success!"),
    new WString("Attention"),
    0);
}
```
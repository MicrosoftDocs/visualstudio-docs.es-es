---
title: API Microsoft.VisualStudio.TestTools.CppUnitTestFramework
ms.date: 06/13/2019
ms.topic: reference
ms.author: mblome
manager: jillfra
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: 3634dcd7cf136aa52de3ebf6bf5bfc3d57632d2c
ms.sourcegitcommit: ab06cde69d862440b4277bcd9bf02e7b50593a1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132142"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Referencia de API Microsoft.VisualStudio.TestTools.CppUnitTestFramework

Este tema se enumeran los miembros públicos de espacio de nombres `Microsoft::VisualStudio::CppUnitTestFramework`. Use estas API para escribir pruebas unitarias de C++ basadas en el marco de pruebas unitarias de tipo nativo de Microsoft. Al final del tema encontrará un [ejemplo de uso](#example).

 Los archivos de encabezado se encuentran en la carpeta _VisualStudio2012[x86]InstallFolder_ **\VC\UnitTest\include**.

 Los archivos lib se encuentran en la carpeta _VisualStudio2012[x86]InstallFolder_ **\VC\UnitTest\lib**.

Las rutas de acceso de encabezado y biblioteca se configuran automáticamente en un proyecto de prueba nativo.

## <a name="In_this_topic"></a> En este tema

[CppUnitTest.h](#cppUnitTest_h)

- [Crear clases y métodos de prueba](#create_test_classes_and_methods)

- [Inicialización y limpieza](#Initialize_and_cleanup)

  - [Métodos de prueba](#test_methods)

  - [Clases de prueba](#test_classes)

  - [Módulos de prueba](#test_modules)

- [Crear atributos de prueba](#create_test_attributes)

  - [Atributos de método de prueba](#test_method_attributes)

  - [Atributos de clase de prueba](#test_class_attributes)

  - [Atributos de módulo de prueba](#test_module_attributes)

  - [Atributos predefinidos](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Aserciones generales](#general_asserts)

    - [Son iguales](#general_are_equal)

    - [No son iguales](#general_are_not_equal)

    - [Son los mismos](#general_are_same)

    - [No son los mismos](#general_are_not_same)

    - [Es Null](#general_is_null)

    - [No es Null](#general_is_not_null)

    - [Es True](#general_is_True)

    - [Es False](#general_is_false)

    - [Error](#general_Fail)

  - [Aserciones en Windows Runtime](#winrt_asserts)

    - [Son iguales](#winrt_are_equal)

    - [Son los mismos](#winrt_are_same)

    - [No son iguales](#winrt_are_not_equal)

    - [No son los mismos](#winrt_are_not_same)

    - [Es Null](#winrt_is_null)

    - [No es Null](#winrt_is_not_null)

  - [Aserciones en excepción](#exception_asserts)

    - [Excepción esperada](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Registrador](#logger)

    - [Escribir mensaje](#write_message)

  - [Ejemplo de uso](#example)

## <a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create_test_classes_and_methods"></a> Crear clases y métodos de prueba

```cpp
TEST_CLASS(className)
```

 Se requiere para cada clase que contiene métodos de prueba. Identifica *className* como una clase de prueba. `TEST_CLASS` debe declararse en el ámbito de espacio de nombres.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

 Define *methodName* como un método de prueba. `TEST_METHOD` debe declararse en el ámbito de la clase del método.

### <a name="Initialize_and_cleanup"></a> Inicialización y limpieza

#### <a name="test_methods"></a> Métodos de prueba

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

 Define *methodName* como un método que se ejecuta antes de ejecutar cada método de prueba. `TEST_METHOD_INITIALIZE` solo se puede definir una vez en una clase de prueba y se debe definir en la clase de prueba.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

 Define *methodName* como un método que se ejecuta después de ejecutar cada método de prueba. `TEST_METHOD_CLEANUP` solo se puede definir una vez en una clase de prueba y se debe definir en el ámbito de la clase de prueba.

#### <a name="test_classes"></a> Clases de prueba

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Define *methodName* como un método que se ejecuta antes de que se cree cada clase de prueba. `TEST_CLASS_INITIALIZE` solo se puede definir una vez en una clase de prueba y se debe definir en el ámbito de la clase de prueba.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Define *methodName* como un método que se ejecuta después de que se cree cada clase de prueba. `TEST_CLASS_CLEANUP` solo se puede definir una vez en una clase de prueba y se debe definir en el ámbito de la clase de prueba.

#### <a name="test_modules"></a> Módulos de prueba

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Define el método *methodName* que se ejecuta cuando se carga un módulo. `TEST_MODULE_INITIALIZE` solo se puede definir una vez en un módulo de prueba y se debe declarar en el ámbito de espacio de nombres.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Define el método *methodName* que se ejecuta cuando se descarga un módulo. `TEST_MODULE_CLEANUP` solo se puede definir una vez en un módulo de prueba y se debe declarar en el ámbito de espacio de nombres.

### <a name="create_test_attributes"></a> Crear atributos de prueba

#### <a name="test_method_attributes"></a> Atributos de método de prueba

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Agrega los atributos definidos con una o varias macros de `TEST_METHOD_ATTRIBUTE` al método de prueba *testMethodName*.

 Una macro de `TEST_METHOD_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.

#### <a name="test_class_attributes"></a> Atributos de clase de prueba

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Agrega los atributos definidos con una o varias macros de `TEST_CLASS_ATTRIBUTE` a la clase de prueba *testClassName*.

 Una macro de `TEST_CLASS_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.

#### <a name="test_module_attributes"></a> Atributos de módulo de prueba

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Agrega los atributos definidos con una o varias macros de `TEST_MODULE_ATTRIBUTE` al módulo de prueba *testModuleName*.

 Una macro de `TEST_MODULE_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.

#### <a name="pre_defined_attributes"></a> Atributos predefinidos

 Estas macros de atributo predefinidas se proporcionan para mayor comodidad en los casos comunes. Se pueden sustituir por la macro `TEST_METHOD_ATTRIBUTE` descrita anteriormente.

```cpp
TEST_OWNER(ownerAlias)
```

 Define un `TEST_METHOD_ATTRIBUTE` con el nombre `Owner` y el valor del atributo de *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Define un `TEST_METHOD_ATTRIBUTE` con el nombre `Description` y el valor del atributo de *description*.

```cpp
TEST_PRIORITY(priority)
```

 Define un `TEST_METHOD_ATTRIBUTE` con el nombre `Priority` y el valor del atributo de *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Define un `TEST_METHOD_ATTRIBUTE` con el nombre `WorkItem` y el valor del atributo de *workItem*.

```cpp
TEST_IGNORE()
```

 Define un `TEST_METHOD_ATTRIBUTE` con el nombre `Ignore` y el valor del atributo de `true`.

## <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general_asserts"></a> Aserciones generales

#### <a name="general_are_equal"></a> Son iguales
 Comprobar que dos objetos son iguales

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos duplicados son iguales

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos floats son iguales

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos cadenas char* son iguales

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos cadenas w_char* son iguales

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_equal"></a> No son iguales
 Comprobar que dos duplicados no son iguales

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos floats no son iguales

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos cadenas char* no son iguales

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Comprobar que dos cadenas w_char* no son iguales

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Compruebe si dos referencias son iguales según el operador ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_same"></a> Son los mismos
 Compruebe que las dos referencias hacen referencia a la misma instancia de objeto (identidad).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_same"></a> No son los mismos
 Compruebe que las dos referencias no hacen referencia a la misma instancia de objeto (identidad).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_null"></a> Es Null
 Compruebe que el puntero es NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_not_null"></a> No es Null
 Compruebe que un puntero no es NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_True"></a> Es True
 Compruebe que una condición es true

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_false"></a> Es False
 Compruebe que una condición es false

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_Fail"></a> Error
 Fuerce el resultado del caso de prueba a producir un error

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="winrt_asserts"></a> Aserciones en Windows Runtime

#### <a name="winrt_are_equal"></a> Son iguales
 Comprueba si dos punteros de Windows Runtime son iguales.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Comprueba que dos cadenas Platform:: String ^ son iguales.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_same"></a> Son los mismos
 Comprueba que dos referencias de Windows Runtime hacen referencia al mismo objeto.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_equal"></a> No son iguales
 Comprueba si dos punteros de Windows Runtime no son iguales.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Comprueba que dos cadenas Platform:: String ^ no son iguales.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_same"></a> No son los mismos
 Comprueba que dos referencias de Windows Runtime no hacen referencia al mismo objeto.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_null"></a> Es Null
 Comprueba que un puntero de Windows Runtime es nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_not_null"></a> No es Null
 Comprueba que un puntero de Windows Runtime no es nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception_asserts"></a> Aserciones en excepción

#### <a name="expect_exception"></a> Excepción esperada
 Compruebe que una función produce una excepción:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Compruebe que una función produce una excepción:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a> Registrador
 La clase Logger contiene métodos estáticos para escribir en la **Ventana de salida**.

### <a name="write_message"></a> Escribir mensaje
Escribir una cadena en la **Ventana de salida**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Ejemplo
 Este código es un ejemplo de uso de VSCppUnit. Incluye ejemplos de metadatos de atributo, accesorios, pruebas unitarias con aserciones y registro personalizado.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Escritura de pruebas unitarias para C/C++](writing-unit-tests-for-c-cpp.md)

---
title: Usar Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77bf44460bf9670cc53703fbf3b4836016135999
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705874"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Usar Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tema se enumeran los miembros públicos de espacio de nombres `Microsoft::VisualStudio::CppUnitTestFramework`.  
  
 Los archivos de encabezado se encuentran en la carpeta _VisualStudio2012[x86]InstallFolder_**\VC\UnitTest\include**.  
  
 Los archivos lib se encuentran en la carpeta _VisualStudio2012[x86]InstallFolder_**\VC\UnitTest\lib**.  
  
## <a name="BKMK_In_this_topic"></a> En este tema  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
- [Crear clases y métodos de prueba](#BKMK_Create_test_classes_and_methods)  
  
- [Inicialización y limpieza](#BKMK_Initialize_and_cleanup)  
  
  - [Métodos de prueba](#BKMK_Test_methods)  
  
  - [Clases de prueba](#BKMK_Test_classes)  
  
  - [Módulos de prueba](#BKMK_Test_modules)  
  
- [Crear atributos de prueba](#BKMK_Create_test_attributes)  
  
  - [Atributos de método de prueba](#BKMK_Test_method_attributes)  
  
  - [Atributos de clase de prueba](#BKMK_Test_class_attributes)  
  
  - [Atributos de módulo de prueba](#BKMK_Test_module_attributes)  
  
  - [Atributos predefinidos](#BKMK_Pre_defined_attributes)  
  
    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
  - [Aserciones generales](#BKMK_General_Asserts)  
  
    - [Son iguales](#BKMK_General_Are_Equal)  
  
    - [No son iguales](#BKMK_General_Are_Not_Equal)  
  
    - [Son los mismos](#BKMK_General_Are_Same)  
  
    - [No son los mismos](#BKMK_General_Are_Not_Same)  
  
    - [Es Null](#BKMK_General_Is_Null)  
  
    - [No es Null](#BKMK_General_Is_Not_Null)  
  
    - [Es True](#BKMK_General_Is_True)  
  
    - [Es False](#BKMK_General_Is_False)  
  
    - [Error](#BKMK_General_Fail)  
  
  - [Aserciones en Windows Runtime](#BKMK_WinRT_Asserts)  
  
    - [Son iguales](#BKMK_WinRT_Are_Equal)  
  
    - [Son los mismos](#BKMK_WinRT_Are_Same)  
  
    - [No son iguales](#BKMK_WinRT_Are_Not_Equal)  
  
    - [No son los mismos](#BKMK_WinRT_Are_Not_Same)  
  
    - [Es Null](#BKMK_WinRT_Is_Null)  
  
    - [No es Null](#BKMK_WinRT_Is_Not_Null)  
  
  - [Aserciones en excepción](#BKMK_Exception_Asserts)  
  
    - [Excepción esperada](#BKMK_Expect_Exception)  
  
      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
    - [Registrador](#BKMK_Logger)  
  
    - [Escribir mensaje](#BKMK_Write_Message)  
  
## <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
### <a name="BKMK_Create_test_classes_and_methods"></a> Crear clases y métodos de prueba  
  
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
  
### <a name="BKMK_Initialize_and_cleanup"></a> Inicialización y limpieza  
  
#### <a name="BKMK_Test_methods"></a> Métodos de prueba  
  
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
  
#### <a name="BKMK_Test_classes"></a> Clases de prueba  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Define *methodName* como un método que se ejecuta después de que se cree cada clase de prueba. `TEST_CLASS_INITIALIZE` solo se puede definir una vez en una clase de prueba y se debe definir en el ámbito de la clase de prueba.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Define *methodName* como un método que se ejecuta después de que se cree cada clase de prueba. `TEST_CLASS_CLEANUP` solo se puede definir una vez en una clase de prueba y se debe definir en el ámbito de la clase de prueba.  
  
#### <a name="BKMK_Test_modules"></a> Módulos de prueba  
  
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
  
### <a name="BKMK_Create_test_attributes"></a> Crear atributos de prueba  
  
#### <a name="BKMK_Test_method_attributes"></a> Atributos de método de prueba  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Agrega los atributos definidos con una o varias macros de `TEST_METHOD_ATTRIBUTE` al método de prueba *testClassName*.  
  
 Una macro de `TEST_METHOD_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.  
  
#### <a name="BKMK_Test_class_attributes"></a> Atributos de clase de prueba  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Agrega los atributos definidos con una o varias macros de `TEST_CLASS_ATTRIBUTE` a la clase de prueba *testClassName*.  
  
 Una macro de `TEST_CLASS_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.  
  
#### <a name="BKMK_Test_module_attributes"></a> Atributos de módulo de prueba  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Agrega los atributos definidos con una o varias macros de `TEST_MODULE_ATTRIBUTE` al módulo de prueba *testModuleName*.  
  
 Una macro de `TEST_MODULE_ATTRIBUTE` define un atributo con el nombre *attributeName* y el valor *attributeValue*.  
  
#### <a name="BKMK_Pre_defined_attributes"></a> Atributos predefinidos  
 Estas macros de atributo predefinidas se pueden sustituir por las macros `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` o `TEST_MODULE_ATTRIBUTE` descritas anteriormente.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Define un atributo con el nombre `Owner` y el valor del atributo de *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Define un atributo con el nombre `Description` y el valor del atributo de *description*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Define un atributo con el nombre `Priority` y el valor del atributo de *priority*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Define un atributo con el nombre `WorkItem` y el valor del atributo de *workItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Define un atributo con el nombre `Ignore` y el valor del atributo de `true`.  
  
## <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
### <a name="BKMK_General_Asserts"></a> Aserciones generales  
  
#### <a name="BKMK_General_Are_Equal"></a> Son iguales  
 Comprobar que dos objetos son iguales  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos duplicados son iguales  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos floats son iguales  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos cadenas char* son iguales  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos cadenas w_char* son iguales  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Not_Equal"></a> No son iguales  
 Comprobar que dos duplicados no son iguales  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos floats no son iguales  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos cadenas char* no son iguales  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Comprobar que dos cadenas w_char* no son iguales  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Compruebe si dos referencias son iguales según el operador ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Same"></a> Son los mismos  
 Compruebe que las dos referencias hacen referencia a la misma instancia de objeto (identidad).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Not_Same"></a> No son los mismos  
 Compruebe que las dos referencias no hacen referencia a la misma instancia de objeto (identidad).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_Null"></a> Es Null  
 Compruebe que el puntero es NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_Not_Null"></a> No es Null  
 Compruebe que un puntero no es NULL  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_True"></a> Es True  
 Compruebe que una condición es true  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_False"></a> Es False  
 Compruebe que una condición es false  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Fail"></a> Error  
 Fuerce el resultado del caso de prueba a producir un error  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
### <a name="BKMK_WinRT_Asserts"></a> Aserciones en Windows Runtime  
  
#### <a name="BKMK_WinRT_Are_Equal"></a> Son iguales  
 Comprueba si dos punteros de Windows Runtime son iguales.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Comprueba que dos cadenas Platform:: String ^ son iguales.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Same"></a> Son los mismos  
 Comprueba que dos referencias de Windows Runtime hacen referencia al mismo objeto.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Not_Equal"></a> No son iguales  
 Comprueba si dos punteros de Windows Runtime no son iguales.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Comprueba que dos cadenas Platform:: String ^ no son iguales.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Not_Same"></a> No son los mismos  
 Comprueba que dos referencias de Windows Runtime no hacen referencia al mismo objeto.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Is_Null"></a> Es Null  
 Comprueba que un puntero de Windows Runtime es nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Is_Not_Null"></a> No es Null  
 Comprueba que un puntero de Windows Runtime no es nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
### <a name="BKMK_Exception_Asserts"></a> Aserciones en excepción  
  
#### <a name="BKMK_Expect_Exception"></a> Excepción esperada  
 Compruebe que una función produce una excepción:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Compruebe que una función produce una excepción:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
## <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
### <a name="BKMK_Logger"></a> Registrador  
 La clase de registrador contiene métodos estáticos en los que escribir  
  
```  
class Logger  
```  
  
### <a name="BKMK_Write_Message"></a> Escribir mensaje  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## <a name="example"></a>Ejemplo  
 Este código es un ejemplo de  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
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
 [Hacer una prueba unitaria de su código](../test/unit-test-your-code.md)   
 [Pruebas unitarias de código nativo con el Explorador de pruebas](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Agregar pruebas unitarias a aplicaciones C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)

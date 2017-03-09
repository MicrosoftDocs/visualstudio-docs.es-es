---
title: "Errores del compilador al implementar una clase derivada de CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compilar código fuente, clases derivadas de CObject"
  - "errores [C++]"
  - "errores [C++], compilador"
  - "clase CObject, errores del compilador de las clases derivadas"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Errores del compilador al implementar una clase derivada de CObject
Cuando se implementa una clase derivada de `CObject` y se escribe el código para que deba llamarse al constructor de copias o al operador de asignación de la clase, el compilador puede notificar errores similares a los siguientes:  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Puede reproducir el problema si compila el ejemplo de la sección de código de ejemplo siguiente.  
  
> [!NOTE]
>  El código de ejemplo que se muestra en este artículo genera los siguientes mensajes de error:  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 El motivo de los errores del compilador es que `CObject` declara un constructor de copias privado y un operador de asignación en el archivo AFX.h. Por consiguiente, el compilador no genera un constructor de copias predeterminado y un operador de asignación para la clase derivada de `CObject`. Como el compilador no encuentra estas funciones declaradas en la clase, informa de los errores.  
  
 Para evitar los errores del compilador, debe implementar un constructor de copias y un operador de asignación para la clase derivada de `CObject`. Esto se muestra en el código de ejemplo siguiente. Puede evitar los errores si quita las marcas de comentario de las líneas que se indican en el código de ejemplo.  
  
## Código de ejemplo  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## Vea también  
 [Advertencia del compiladors C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)
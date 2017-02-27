---
title: "IDebugClassField::GetDefaultIndexer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetDefaultIndexer"
helpviewer_keywords: 
  - "IDebugClassField::GetDefaultIndexer (método)"
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre del indizador predeterminado.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```c#  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### Parámetros  
 `pbstrIndexer`  
 \[out\]  Devuelve una cadena que contiene el nombre del indizador predeterminado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay indizador predeterminado.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El indizador predeterminado de una clase es la propiedad que se marca como la propiedad de `Default` para los métodos de la matriz.  Esto es específico de [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  A continuación se muestra un ejemplo de un indizador predeterminado declarado en [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] y cómo se utiliza.  
  
```vb#  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
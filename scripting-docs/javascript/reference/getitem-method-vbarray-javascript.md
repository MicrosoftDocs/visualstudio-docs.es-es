---
title: "getItem (M&#233;todo, VBArray de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getItem"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getItem (método)"
  - "Item (propiedad)"
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getItem (M&#233;todo, VBArray de JavaScript)
Devuelve el elemento en la ubicación especificada.  
  
## Sintaxis  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)  
```  
  
## Parámetros  
 *safeArray*  
 Obligatorio. Objeto VBArray.  
  
 *dimension1, ..., dimensionN*  
 Especifica la ubicación exacta del elemento deseado de VBArray.*n* es igual al número de dimensiones de VBArray.  
  
## Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que itera la matriz segura de Visual Basic e imprime el contenido de cada elemento. Ambas partes van en la sección \<HEAD\> de una página HTML. La tercera parte es el código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que va en la sección \<BODY\> para ejecutar las otras dos partes.  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Requisitos  
 Se admite en los siguientes modos de documento: Interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray \(Objeto\)](../../javascript/reference/vbarray-object-javascript.md)  
  
## Vea también  
 [dimensions \(Método, VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound \(Método, VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray \(Método, VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound \(Método, VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
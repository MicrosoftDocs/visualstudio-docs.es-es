---
title: "lbound (M&#233;todo, VBArray de JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound (método)"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound (M&#233;todo, VBArray de JavaScript)
Devuelve el menor valor de índice que se utiliza en la dimensión especificada de un objeto VBArray.  
  
## Sintaxis  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Parámetros  
 *safeArray*  
 Requerido.  Objeto VBArray.  
  
 `dimension`  
 Opcional.  Dimensión del objeto VBArray para la que se desea obtener el índice del límite inferior.  Si se omite, `lbound` se comporta como si se hubiera pasado 1.  
  
## Comentarios  
 Si el objeto VBArray está vacío, el método `lbound` devuelve el valor undefined.  Si el argumento `dimension` es mayor que el número de dimensiones del objeto VBArray, o es negativo, el método genera un error "Subíndice fuera del intervalo".  
  
## Ejemplo  
 El siguiente ejemplo consta de tres partes.  La primera parte es código VBScript para crear una matriz segura de Visual Basic.  La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que determina el número de dimensiones de la matriz segura y el límite inferior de cada dimensión.  Dado que la matriz segura se crea en VBScript en lugar de en Visual Basic, el límite inferior será siempre cero.  Ambas partes van en la sección \<HEAD\> de una página HTML.  La tercera parte es el código de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que va en la sección \<BODY\> para ejecutar las otras dos partes.  
  
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
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## Requisitos  
 Se admite en los siguientes modos de documento: quirks \(modo de emulación de otros exploradores web\), estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10.  No se admite en aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Vea [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray \(Objeto\)](../../javascript/reference/vbarray-object-javascript.md)  
  
## Vea también  
 [dimensions \(Método, VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem \(Método, VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray \(Método, VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound \(Método, VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
---
title: "ubound (M&#233;todo, VBArray, JavaScript) | Microsoft Docs"
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
  - "ubound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ubound (método)"
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# ubound (M&#233;todo, VBArray, JavaScript)
Devuelve el valor de índice más alto empleado en la dimensión especificada del objeto VBArray.  
  
## Sintaxis  
  
```  
  
safeArray.ubound(dimension)  
```  
  
## Parámetros  
 *safeArray*  
 Obligatorio. Objeto VBArray.  
  
 `dimension`  
 Opcional. Es la dimensión del objeto VBArray para la que se quiere el índice del límite más alto. Si se omite, `ubound` se comporta como si se hubiera pasado un 1.  
  
## Comentarios  
 Si el objeto VBArray está vacío, el método `ubound` devuelve undefined. Si `dim` es mayor que el número de dimensiones del objeto VBArray, o bien es negativo, el método genera un error "El subíndice está fuera del intervalo".  
  
## Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que determina el número de dimensiones en la matriz segura y el límite superior de cada dimensión. Ambas partes van en la sección \<HEAD\> de una página HTML. La tercera parte es el código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que va en la sección \<BODY\> para ejecutar las otras dos partes.  
  
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
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
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
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray \(Objeto\)](../../javascript/reference/vbarray-object-javascript.md)  
  
## Vea también  
 [dimensions \(Método, VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem \(Método, VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound \(Método, VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray \(Método, VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)
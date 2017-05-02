---
title: "VBArray (Objeto de JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "VBArray (constante de objeto)"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# VBArray (Objeto de JavaScript)
Permite acceder a las matrices seguras de Visual Basic.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer, no con las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintaxis  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## Parámetros  
 `varName`  
 Obligatorio. Nombre de variable a la que se asigna VBArray.  
  
 *safeArray*  
 Obligatorio. Valor VBArray.  
  
## Comentarios  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. Antes de pasarse al constructor VBArray, el argumento *safeArray* debe haber obtenido un valor VBArray. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
 Los elementos VBArray pueden tener varias dimensiones. Los índices de cada dimensión pueden ser diferentes. El método **dimensions** recupera el número de dimensiones de la matriz; los métodos `lbound` y `ubound` recuperan el intervalo de índices usado por cada dimensión.  
  
## Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que convierte la matriz segura de Visual Basic en una matriz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Ambas partes van en la sección \<HEAD\> de una página HTML. La tercera parte es el código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que va en la sección \<BODY\> para ejecutar las otras dos partes.  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## Propiedades  
 El objeto `VBArray` no tiene propiedades.  
  
## Métodos  
 [dimensions \(método\)](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem \(método\)](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound \(método\)](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray \(método\)](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound \(método\)](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## Requisitos  
 Se admite en los siguientes modos de documento: Interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
## Vea también  
 [Array \(Objeto\)](../../javascript/reference/array-object-javascript.md)
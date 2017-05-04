---
title: "dimensions (M&#233;todo, VBArray de JavaScript) | Microsoft Docs"
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
  - "dimensions"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dimensions (método)"
  - "VBArray (constante de objeto)"
ms.assetid: ac83589e-85d9-48cb-b28d-c579e65fd604
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# dimensions (M&#233;todo, VBArray de JavaScript)
Devuelve el número de dimensiones de un objeto VBArray.  
  
## Sintaxis  
  
```  
  
array.dimensions( )  
```  
  
## Comentarios  
 La *matriz* necesaria es un objeto VBArray.  
  
## Ejemplo  
 El método **dimensions** proporciona una forma de recuperar el número de dimensiones en un objeto VBArray especificado.  
  
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
   return(s);  
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
 [getItem \(Método, VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound \(Método, VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray \(Método, VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound \(Método, VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)
---
title: "toArray (método, VBArray) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>toArray (Método, VBArray de JavaScript)
Devuelve una matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estándar convertida de un objeto VBArray.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Comentarios  
 La referencia *safeArray* necesaria es un objeto VBArray.  
  
 La conversión traslada el objeto VBArray multidimensional a una matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] unidimensional. Cada dimensión sucesiva se anexa al final de la anterior. Por ejemplo, un objeto VBArray con tres dimensiones y tres elementos en cada dimensión se convierte en una matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tal como se muestra a continuación:  
  
 Supongamos que el objeto VBArray contiene: (1, 2, 3), (4, 5, 6), (7, 8, 9). Después de la traslación, la matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contiene: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Actualmente no hay manera de convertir una matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en un objeto VBArray.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que convierte la matriz segura de Visual Basic en una matriz de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Ambas partes van en la \<HEAD > sección de una página HTML. La tercera parte es el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que va en la \<BODY > para ejecutar las otras dos partes.  
  
```JavaScript  
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
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray)  
{  
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
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Dimensions (método, VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem (método, VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [LBound (método, VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound (Método, VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
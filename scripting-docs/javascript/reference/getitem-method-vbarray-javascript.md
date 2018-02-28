---
title: "getItem (método, VBArray) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem (Método, VBArray de JavaScript)
Devuelve el elemento en la ubicación especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Parámetros  
 *safeArray*  
 Obligatorio. Objeto VBArray.  
  
 *dimension1, ..., dimensionN*  
 Especifica la ubicación exacta del elemento deseado de VBArray. *n* es igual al número de dimensiones de VBArray.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es código [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que itera la matriz segura de Visual Basic e imprime el contenido de cada elemento. Ambas partes van en la \<HEAD > sección de una página HTML. La tercera parte es el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que va en la \<BODY > para ejecutar las otras dos partes.  
  
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
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Dimensions (método, VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [LBound (método, VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray (método, VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound (Método, VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
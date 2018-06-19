---
title: LBound (método, VBArray) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638205"
---
# <a name="lbound-method-vbarray-javascript"></a>lbound (Método, VBArray de JavaScript)
Devuelve el valor de índice más bajo utilizado en la dimensión especificada de un objeto VBArray.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>Parámetros  
 *safeArray*  
 Obligatorio. Objeto VBArray.  
  
 `dimension`  
 Opcional. La dimensión del objeto VBArray para la que se desea el índice de límite inferior. Si se omite, `lbound` se comporta como si se hubiera pasado un 1.  
  
## <a name="remarks"></a>Comentarios  
 Si el objeto VBArray está vacío, el método `lbound` devuelve undefined. Si `dimension` es mayor que el número de dimensiones del objeto VBArray, o bien es negativo, el método genera un error "El subíndice está fuera del intervalo".  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo consta de tres partes. La primera parte es código VBScript para crear una matriz segura de Visual Basic. La segunda parte es [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que determina el número de dimensiones de la matriz segura y el límite inferior de cada dimensión. Puesto que la matriz segura se crea en VBScript en lugar de Visual Basic, el límite inferior siempre será cero. Ambas partes van en la \<HEAD > sección de una página HTML. La tercera parte es el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que va en la \<BODY > para ejecutar las otras dos partes.  
  
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
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Dimensions (método, VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem (método, VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray (método, VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound (Método, VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)
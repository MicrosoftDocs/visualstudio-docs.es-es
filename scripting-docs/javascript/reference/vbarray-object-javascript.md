---
title: VBArray (objeto) (JavaScript) | Documentos de Microsoft
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
- VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-object-javascript"></a>VBArray (Objeto de JavaScript)
Permite acceder a las matrices seguras de Visual Basic.  
  
> [!WARNING]
>  Este objeto solo es compatible con Internet Explorer, no con las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Parámetros  
 `varName`  
 Obligatorio. Nombre de variable a la que se asigna VBArray.  
  
 *safeArray*  
 Obligatorio. Valor VBArray.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos VBArray son de solo lectura y no se pueden crear directamente. Antes de pasarse al constructor VBArray, el argumento *safeArray* debe haber obtenido un valor VBArray. Esto solo se puede hacer si se recupera el valor de un objeto ActiveX u otro existente.  
  
 Los elementos VBArray pueden tener varias dimensiones. Los índices de cada dimensión pueden ser diferentes. El método **dimensions** recupera el número de dimensiones de la matriz; los métodos `lbound` y `ubound` recuperan el intervalo de índices usado por cada dimensión.  
  
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
  
## <a name="properties"></a>Propiedades  
 El objeto `VBArray` no tiene propiedades.  
  
## <a name="methods"></a>Métodos  
 [Dimensions (método)](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem (método)](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound (método)](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray (método)](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound (método)](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Vea también  
 [Array (Objeto)](../../javascript/reference/array-object-javascript.md)
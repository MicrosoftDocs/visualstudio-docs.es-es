---
title: Función String.raw (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640165"
---
# <a name="stringraw-function-javascript"></a>Función String.raw (JavaScript)
Devuelve la forma de cadena sin formato de una cadena de plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `templateStr`  
 Obligatorio. Cadena de la plantilla.  
  
 `obj`  
 Obligatorio. Un objeto formado correctamente especificado mediante la notación literal de objeto, como {raw: 'valor'}.  
  
 `...substitutions`  
 Opcional. Una matriz (un [rest, parámetro](../../javascript/functions-javascript.md)) que consta de uno o más valores de sustitución.  
  
## <a name="remarks"></a>Comentarios  
 El `String.raw` función está pensada para su uso con [cadenas de plantillas de](../../javascript/advanced/template-strings-javascript.md). La cadena sin formato incluirá todos los caracteres de escape y barras diagonales inversas que se encuentren en la cadena.  
  
 Se produce un error si `obj` no es un objeto bien formado.  
  
## <a name="example"></a>Ejemplo  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
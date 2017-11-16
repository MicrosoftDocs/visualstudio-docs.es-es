---
title: Advertencias de VSInstr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4ef9833b61a88fe45d9293cd036a52ce74788d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vsinstr-warnings"></a>Advertencias de VSInstr
La tabla siguiente muestra las advertencias emitidas por la herramienta VSInstr.exe. Para evitar que aparezca una advertencia, utilice su número con la opción NOWARN.  
  
|Número de advertencia|Descripción|  
|--------------------|-----------------|  
|**VSP2000**|Error interno No se puede obtener el nombre del archivo de módulo para este archivo ejecutable.|  
|**VSP2001**|\<nombre del ensamblado> es un ensamblado de nombre seguro. Deberá volver a firmarlo antes de que pueda ejecutarse.<br /><br /> Esta advertencia aparece cuando se instrumenta un ensamblado firmado. Puede utilizar la herramienta sn.exe para volver a firmar el archivo binario o desactivar temporalmente el requisito de nombre seguro. Para obtener más información, vea [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|No se pudo encontrar la función \<nombre de función> en el archivo \<nombre de archivo><br /><br /> Esta advertencia se produce cuando no se encuentra una función en el archivo especificado.|  
|**VSP2003**|No se pudo encontrar ningún salto cruzado a la \<nombre de función> en el archivo \<nombre de archivo>.<br /><br /> Esta advertencia se produce si VSInstr no puede anular saltos cruzados. Los saltos cruzados se usan para la optimización del código.|  
|**VSP2004**|Se excluyó la función \<nombre de función> mediante el modificador de la línea de comandos EXCLUDE pero era necesaria porque contenía un salto cruzado.<br /><br /> Esta advertencia se produce si la función se excluyó mediante la opción EXCLUDE pero se necesita durante el proceso de instrumentación. El generador de perfiles incluye automáticamente la función necesaria.|  
|**VSP2005**|Error de instrumentación interno \<texto de error><br /><br /> Esta advertencia se emite si no se puede realizar la instrumentación. Revise el texto de error para determinar si puede corregirse.|  
|**VSP2006**|No se pudo encontrar PDB para \<nombre><br /><br /> Esta advertencia aparece si el archivo PDB no existe en la ruta de búsqueda o no coincide con el binario.|  
|**VSP2007**|\<nombre de archivo> no contiene código instrumentable.<br /><br /> Esta advertencia se emite si se han excluido todas las funciones del archivo binario o si el archivo especificado solo contiene recursos.|  
|**VSP2008**|No se pueden obtener los atributos de seguridad de \<nombre>. Código de error \<código><br /><br /> Esta advertencia se produce si el usuario no tiene el permiso READ_DAC. Durante el proceso de instrumentación, el generador de perfiles intenta conservar la DACL original del binario. Dado que el archivo binario original se reemplaza por otro nuevo, la DACL del archivo binario original se debe copiar y aplicar al nuevo. Esto puede producir un error si el usuario no tiene acceso de READ_DAC para el archivo binario original.|  
|**VSP2009**|No se pueden establecer los atributos de seguridad en \<nombre>. Código de error \<número de error ><br /><br /> Esta advertencia se produce si el usuario no tiene el permiso WRITE_DAC. Durante el proceso de instrumentación, el generador de perfiles intenta conservar la DACL original del binario. Dado que el archivo binario original se reemplaza por otro nuevo, la DACL del archivo binario original se debe copiar y aplicar al nuevo. Esto puede producir un error si el usuario no tiene acceso de WRITE_DAC para el nuevo archivo binario.|  
|**VSP2010**|No se seleccionaron funciones específicamente para la instrumentación debido a las opciones -INCLUDE/-EXCLUDE.|  
|**VSP2011**|Las funciones específicas incluir o excluir \<nombre> no coinciden con ninguna función.|  
|**VSP2012**|La imagen no contiene ningún código que se pueda instrumentar para cobertura de código.<br /><br /> El generador de perfiles no instrumenta el tipo de código siguiente:<br /><br /> - Funciones CRT estáticas<br />- Métodos administrados atribuidos con NonUserCodeAttribute<br />- Métodos administrados atribuidos con DebuggerHiddenAttribute<br />- Bloques MASM<br /><br /> Esta advertencia se genera si, después de este filtrado, no queda código.|  
|**VSP2013**|La instrumentación de esta imagen requiere que se ejecute como un proceso de 32 bits. Los marcadores de encabezado de CLR se actualizaron para reflejar esta condición.<br /><br /> El generador de perfiles modifica el binario para que los sistemas operativos de 64 bits puedan abrir el proceso de 32 bits en el emulador WOW64. Esto podría dar error con las bibliotecas (archivos DLL) si se cargan en un proceso de 64 bits existente. Esta advertencia notifica al usuario la existencia de esta dependencia.|  
|**VSP2014**|La imagen instrumentada resultante no parece ser válida y puede que no se ejecute.<br /><br /> Este mensaje aparece cuando el ensamblado instrumentado final tiene un encabezado de PE no válido.|  
  
## <a name="see-also"></a>Vea también  
 [VSInstr](../profiling/vsinstr.md)
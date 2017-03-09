---
title: "Advertencias de VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instrumentación, VSInstr (herramienta)"
  - "herramientas de rendimiento, VSInstr (herramienta)"
  - "VSInstr (herramienta)"
  - "advertencias"
  - "advertencias, VSInstr (herramienta)"
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Advertencias de VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tabla siguiente muestra las advertencias emitidas por la herramienta VSInstr.exe.  Para evitar que aparezca una advertencia, utilice su número con la opción NOWARN.  
  
|Número de advertencia|Descripción|  
|---------------------------|-----------------|  
|**VSP2000**|Error interno.  No se puede obtener el nombre del archivo de módulo para este archivo ejecutable.|  
|**VSP2001**|\<el nombre\> del ensamblado es un ensamblado de nombre seguro.  Deberá volver a firmarlo antes de que pueda ejecutarse.<br /><br /> Esta advertencia aparece cuando se instrumenta un ensamblado firmado.  Puede utilizar la herramienta sn.exe para volver a firmar el archivo binario o desactivar temporalmente el requisito de nombre seguro.  Para obtener más información, vea [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).|  
|**VSP2002**|No encuentra el funcname \<de la función\> en nombre del \<archivo\><br /><br /> Esta advertencia se produce cuando no se encuentra una función en el archivo especificado.|  
|**VSP2003**|No se encontró ninguna saltos cruzada al \<funcname de la función\> en nombre \<del archivo\>.<br /><br /> Esta advertencia se produce si VSInstr no puede anular los saltos cruzados.  Los saltos del cruce se utilizan para la optimización del código.|  
|**VSP2004**|El funcname \<de función\> se excluyó mediante el modificador de línea de comandos EXCLUDE aunque obligatoria porque contiene un salto cruzado.<br /><br /> Esta advertencia aparece si la función se ha excluido utilizando la opción EXCLUDE, pero se necesita durante el proceso de instrumentación.  El generador de perfiles incluye la función necesaria automáticamente.|  
|**VSP2005**|Texto interno de \<error de instrumentación\><br /><br /> Esta advertencia se emite si no se puede realizar la instrumentación.  Revise el texto del error para determinar si se puede corregir.|  
|**VSP2006**|No puede encontrar la PDB para \<el nombre\><br /><br /> Esta advertencia aparece si el archivo PDB no existe en la ruta de búsqueda o no coincide con el binario.|  
|**VSP2007**|\<el nombre de archivo\> no contiene ningún código instrumentable.<br /><br /> Esta advertencia se emite si se han excluido todas las funciones del archivo binario o si el archivo especificado sólo contiene recursos.|  
|**VSP2008**|No se puede obtener atributos de \<seguridad de nombre\>.  Código \<del código de error\><br /><br /> Esta advertencia se produce si el usuario no tiene el permiso de READ\_DAC.  Durante el proceso de instrumentación, el generador de perfiles intenta conservar la DACL original del binario.  Dado que el binario original se reemplaza por otro nuevo, la DACL debe copiarse y aplicarse al nuevo.  Esto puede fallar si el usuario no tiene acceso de READ\_DAC para el binario original.|  
|**VSP2009**|No se puede establecer atributos de seguridad en \<nombre\>.  Número \<de error del código de error\><br /><br /> Esta advertencia se produce si el usuario no tiene el permiso de WRITE\_DAC.  Durante el proceso de instrumentación, el generador de perfiles intenta conservar la DACL original del binario.  Dado que el binario original se reemplaza por otro nuevo, la DACL debe copiarse y aplicarse al nuevo.  Esto puede fallar si el usuario no tiene acceso de WRITE\_DAC para el binario original.|  
|**VSP2010**|No se seleccionaron funciones específicamente para la instrumentación debido a las opciones \/INCLUIR o \/EXCLUIR.|  
|**VSP2011**|El nombre de funcspec de inclusión\/ \<Exclude\> no coincide con ninguna funciones|  
|**VSP2012**|La imagen no contiene ningún código que se pueda instrumentar para cobertura de código.<br /><br /> El generador de perfiles no instrumenta el tipo de código siguiente:<br /><br /> -   Funciones CRT estáticas<br />-   Métodos administrados atribuidos con NonUserCodeAttribute<br />-   Métodos administrados atribuidos con DebuggerHiddenAttribute<br />-   Bloques MASM<br /><br /> Esta advertencia se genera si, después de este filtrado, no queda código.|  
|**VSP2013**|Para instrumentar esta imagen es necesario que se ejecute como un proceso de 32 bits.  Las marcas de encabezado de CLR se actualizaron para reflejar esto.<br /><br /> El generador de perfiles modifica el binario para que los sistemas operativos de 64 bits puedan abrir el proceso de 32 bits en el emulador WOW64.  Esto podría fallar con las bibliotecas \(archivos DLL\) si se cargan en un proceso de 64 bits existente.  Esta advertencia notifica al usuario la existencia de esta dependencia.|  
|**VSP2014**|La imagen instrumentada resultante no parece ser válida y puede que no se ejecute.<br /><br /> Este mensaje aparece cuando el ensamblado instrumentado final tiene un encabezado de PE no válido.|  
  
## Vea también  
 [VSInstr](../profiling/vsinstr.md)
---
title: Asistente (. Archivo vsz) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7f4abe6240f799ed6db71fcf04a40774facaf6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-vsz-file"></a>Asistente (. Archivo vsz)
El entorno de desarrollo integrado (IDE) utiliza archivos .vsz para iniciar a asistentes. Estos archivos .vsz contienen información que el IDE se usa para determinar qué asistente al que llamar y qué información va a pasar al asistente.  
  
 Un archivo .vsz es una versión de un archivo de texto con formato .ini que tiene secciones. Se almacena información conocida por el IDE al principio del archivo. Esto proporciona un vínculo entre el Asistente para la que llama el IDE y los parámetros que se encuentran en el archivo .vsz va a pasar al IDE. El resto del archivo proporciona los parámetros que son específicos para el asistente y que se sea recopilado por el IDE y se pasa al Asistente específico.  
  
 En el ejemplo siguiente se muestra el contenido de un archivo .vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 A continuación se indican los componentes en el archivo .vsz.  
  
|Parte|Descripción|  
|----------|-----------------|  
|VSWizard|El primer parámetro en el archivo es el número de versión del formato del archivo de plantilla. Este número de versión debe ser 6.0, 7.0, 7.1 o 8.0. El resto de números no se puede iniciar y producirá un error de formato no válido.|  
|Asistente|Este campo contiene el ProgID de OLE del asistente, o también una representación de cadena GUID del CLSID del asistente que le por el IDE.|  
|Parám|Estas partes son opcionales. Puede agregar tantas como sea necesario.|  
  
 Los parámetros permiten al archivo .vsz pasar parámetros personalizados adicionales al asistente. Cada valor se pasa como un elemento de cadena en una matriz de elementos Variant en el asistente. Para obtener más información, consulte [Custom Parameters](../../extensibility/internals/custom-parameters.md). Para obtener información sobre cómo usar un archivo .vsz en el desarrollo de asistentes personalizados, consulte [. Archivo vsz (Control del proyecto)](/cpp/ide/dot-vsz-file-project-control)  
  
 Para agregar un identificador de configuración regional predeterminada para el archivo .vsz, especifique `FALLBACK_LCID`= xxxx, donde xxxx es el identificador de configuración regional, por ejemplo, 1033 para inglés. Cuando `FALLBACK_LCID` se define el parámetro, el asistente utiliza el identificador de configuración regional de reserva proporcionado si no se encuentra el Id. actual.  
  
## <a name="see-also"></a>Vea también  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
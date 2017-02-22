---
title: "Asistente (. Archivo vsz) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vsz (archivos)"
  - "vsz (archivos)"
  - "asistentes, archivos"
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Asistente (. Archivo vsz)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno \(IDE\) de desarrollo integrado utiliza archivos .vsz para iniciar asistentes.  Estos archivos .vsz contienen información que usa el IDE para determinar qué asistente a llamar y qué información al asistente.  
  
 Un archivo .vsz es una versión de un archivo de texto de .ini\-formatted que no tiene ninguna sección.  Información conocida al IDE se almacena al principio del archivo.  Esto proporciona un vínculo entre el asistente que las llamadas del IDE y parámetros que están en el archivo .vsz que se pasará al IDE.  El resto del archivo proporciona los parámetros que son específicos del asistente y que deben recolectarse por el IDE y pasar el asistente concreto.  
  
 El ejemplo siguiente muestra el contenido de un archivo .vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Los siguientes son las partes en el archivo .vsz.  
  
|Parte|Descripción|  
|-----------|-----------------|  
|VSWizard|El primer parámetro del archivo es el número de versión del formato de archivo de plantilla.  El número de versión debe ser 6,0, 7,0, 7,1, 8,0.  Otros números no pueden ser encendidos y producir un error de formato de Invalid.|  
|Wizard|Este campo contiene ProgID OLE del asistente, o también una representación de cadena GUID del CLSID del asistente que cocreated por el IDE.|  
|Param|Estas partes son opcionales.  Puede agregar tanto como sea necesario.|  
  
 Los parámetros permiten el archivo .vsz pase parámetros personalizados adicionales al asistente.  Cada valor se pasa como elemento de cadena en una matriz de variantes el asistente.  Para obtener más información, vea [Parámetros personalizados](../../extensibility/internals/custom-parameters.md).  Para obtener información sobre cómo utilizar un archivo .vsz en el desarrollo de asistentes personalizados, vea [Archivo .vsz \(Control del proyecto\)](/visual-cpp/ide/dot-vsz-file-project-control)  
  
 Para agregar un identificador de configuración regional predeterminado en el archivo .vsz, especifique el \=xxxx de `FALLBACK_LCID`, donde es el identificador de configuración regional xxxx, por ejemplo, 1033 para inglés.  Cuando el parámetro de `FALLBACK_LCID` está definido, el asistente utiliza el identificador de configuración regional proporcionado de reserva si el identificador actual no se encuentra.  
  
## Vea también  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Descripción del directorio de plantilla \(. Archivos VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
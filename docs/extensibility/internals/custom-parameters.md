---
title: "Par&#225;metros personalizados | Microsoft Docs"
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
  - "asistentes, parámetros personalizados"
  - "parámetros personalizados"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Par&#225;metros personalizados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los parámetros personalizados controlan la operación de un asistente después de que un asistente comience.  Un archivo relacionado .vsz proporciona una matriz de los parámetros definidos por el usuario que están empaquetados por el entorno de desarrollo integrado \(IDE\) \(IDE\) y se pasan al asistente como una matriz de cadenas cuando se inicia el asistente.  El asistente después analiza la matriz de cadenas y utiliza la información para controlar la operación real del asistente.  De esta manera, un asistente puede personalizar funcionalidad dependiendo del contenido del archivo .vsz.  
  
 Los parámetros de contexto, por otra parte, defina el estado del proyecto cuando se inicia el asistente.  Para obtener más información, vea [Parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
 A continuación se muestra un ejemplo de un archivo .vsz con parámetros personalizados:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 El autor del archivo .vsz agrega los valores de los parámetros.  Cuando un usuario selecciona **Nuevo proyecto** o **Agregar nuevo elemento** en el menú archivo o haciendo clic con el botón secundario en un proyecto en **Explorador de soluciones**, el IDE obtiene estos valores en una matriz de cadenas.  El IDE llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> de proyectos con la marca de <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> , y el proyecto llama al método de <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> responsable de ejecutar el asistente y devolver el resultado.  
  
 El asistente es responsable de analizar la matriz de cadenas y de la que actúe en cadenas correctamente.  De esta manera, implementando parámetros personalizados puede crear un asistente que realiza varias funciones.  Es decir un asistente puede tener tres diferentes archivos .vsz.  Cada archivo pasa diferentes conjuntos de parámetros personalizados para controlar el comportamiento del asistente en diversas situaciones.  
  
 Para obtener más información, vea [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)
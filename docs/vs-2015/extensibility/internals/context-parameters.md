---
title: Parámetros de contexto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 663583129453fc8bd9b71c2be2337a5528f9f7d9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238089"
---
# <a name="context-parameters"></a>Parámetros de contexto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE), puede agregar asistentes a la **nuevo proyecto**, **Agregar nuevo elemento**, o **agregar subproyecto** cuadros de diálogo. Están disponibles en los asistentes que se ha agregado el **archivo** menú o con el botón secundario en un proyecto de **el Explorador de soluciones**. El IDE pasa los parámetros de contexto para la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama el asistente.  
  
 Inicie el IDE de asistentes estableciendo el <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca en la llamada del IDE a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método para el proyecto. Cuando se establece, el proyecto debe hacer que el `IVsExtensibility::RunWizardFile` método que se ejecutará con el nombre del asistente registrado o GUID y otros parámetros de contexto que el IDE le pasa.  
  
## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardNewProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementación, el GUID para el asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nombre del proyecto.|  
|`LocalDirectory`|Ubicación local de archivos de proyecto de trabajo.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es la instalación.|  
|`FExclusive`|Marca booleana que indica que el proyecto debe cerrar soluciones que estén abiertas.|  
|`SolutionName`|Nombre del archivo de solución sin la parte del directorio o la extensión .sln. El nombre de archivo .suo también se crea mediante el uso de `SolutionName`. Si este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si este nombre es una cadena vacía, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddItem>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementación, el GUID para el asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nombre del proyecto.|  
|`ProjectItems`|Ubicación local que contiene los archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo vsdir. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es la instalación.|  
|`Silent`|Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para agregar subproyecto.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] implementación, el GUID para el asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nombre del proyecto.|  
|`ProjectItems`|Puntero a la `ProjectItems` colección en el que funciona el asistente. Este puntero se pasa al Asistente basándose en la selección de jerarquía del proyecto. Un usuario normalmente selecciona una carpeta en la que se va a colocar el elemento y, a continuación, llama el proyecto **Agregar elemento** cuadro de diálogo.|  
|`LocalDirectory`|Ubicación local de archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo vsdir. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es la instalación.|  
|`Silent`|Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parámetros de contexto para iniciar asistentes](http://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)


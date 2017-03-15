---
title: "Parámetros de contexto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>Parámetros de contexto
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE), puede agregar asistentes a la **nuevo proyecto**, **Agregar nuevo elemento**, o **agregar subproyecto** cuadros de diálogo. Los asistentes agregados están disponibles en la **archivo** menú o haciendo clic en un proyecto en **el Explorador de soluciones**. El IDE pasa los parámetros de contexto para la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama el asistente.  
  
 Inicia el IDE de asistentes estableciendo la <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>marca en la llamada del IDE a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>método para el proyecto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Cuando se establece, el proyecto debe hacer el `IVsExtensibility::RunWizardFile` método que va a ejecutar utilizando el nombre del asistente registrado o GUID y otros parámetros de contexto que le pasa el IDE.  
  
## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardNewProject>) o el GUID que indica el tipo de asistente.</xref:EnvDTE.Constants.vsWizardNewProject> En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`LocalDirectory`|Ubicación local de los archivos de proyecto de trabajo.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`FExclusive`|Indicador booleano que indica que el proyecto debe cerrar las soluciones abiertas.|  
|`SolutionName`|Nombre del archivo de solución sin la extensión .sln o de parte del directorio. El nombre de archivo .suo también se crea mediante `SolutionName`. Si este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A>antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A>.</xref:EnvDTE._Solution.AddFromTemplate%2A> </xref:EnvDTE._Solution.Create%2A> Si este nombre es una cadena vacía, utilice <xref:EnvDTE._Solution.AddFromTemplate%2A>sin llamar a <xref:EnvDTE._Solution.Create%2A>.</xref:EnvDTE._Solution.Create%2A> </xref:EnvDTE._Solution.AddFromTemplate%2A>|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddItem>) o el GUID que indica el tipo de asistente.</xref:EnvDTE.Constants.vsWizardAddItem> En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la implementación, el GUID para el asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`ProjectItems`|Ubicación local que contiene los archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo vsdir. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para agregar subproyecto  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o el GUID que indica el tipo de asistente.</xref:EnvDTE.Constants.vsWizardAddSubProject> En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la implementación, el GUID para el asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`ProjectItems`|Puntero a la `ProjectItems` colección en la que funciona el asistente. Este puntero se pasa al Asistente basándose en la selección de jerarquía del proyecto. Un usuario normalmente selecciona una carpeta en la que colocar el elemento y, a continuación, llama el proyecto **Agregar elemento** cuadro de diálogo.|  
|`LocalDirectory`|Ubicación local de los archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo vsdir. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en modo silencioso como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parámetros de contexto para iniciar asistentes](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)

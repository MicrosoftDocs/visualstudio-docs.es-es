---
title: Parámetros de contexto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb6646e917b4cb94b4cd0534b513d148490cf69d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="context-parameters"></a>Parámetros de contexto
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), puede agregar el asistentes para la **nuevo proyecto**, **Agregar nuevo elemento**, o **Agregar proyecto de Sub** cuadros de diálogo. Los asistentes agregados están disponibles en la **archivo** menú o haciendo clic en un proyecto en **el Explorador de soluciones**. El IDE pasa parámetros de contexto a la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama el asistente.  
  
 Inicia el IDE de asistentes estableciendo la <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca en la llamada del IDE a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método para el proyecto. Cuando se establece, el proyecto debe hacer el `IVsExtensibility::RunWizardFile` método al que se pueden ejecutar con el nombre del asistente registrado o GUID y otros parámetros de contexto que el IDE le pasa.  
  
## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Asistente para tipo registrado (<xref:EnvDTE.Constants.vsWizardNewProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`LocalDirectory`|Ubicación local de archivos de proyecto de trabajo.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`FExclusive`|Marca booleana que indica que el proyecto debería cerrar soluciones que estén abiertas.|  
|`SolutionName`|Nombre del archivo de solución sin la extensión .sln o de parte del directorio. El nombre de archivo .suo también se crea mediante el uso de `SolutionName`. Si este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si este nombre es una cadena vacía, utilice <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en segundo plano como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Asistente para tipo registrado (<xref:EnvDTE.Constants.vsWizardAddItem>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`ProjectItems`|Ubicación local que contiene los archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que va a agregarse. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en segundo plano como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para el proyecto de complemento Sub  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WizardType`|Asistente para tipo registrado (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto.|  
|`ProjectItems`|Puntero a la `ProjectItems` colección en el que el asistente funciona. Este puntero se pasa al Asistente basándose en la selección de jerarquía del proyecto. Un usuario normalmente selecciona una carpeta en la que se va a colocar el elemento y, a continuación, llama el proyecto **Agregar elemento** cuadro de diálogo.|  
|`LocalDirectory`|Ubicación local de archivos de proyecto de trabajo.|  
|`ItemName`|Nombre del elemento que va a agregarse. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el archivo. El nombre puede ser un valor null.|  
|`InstallationDirectory`|Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación.|  
|`Silent`|Un valor booleano que indica si el asistente debe ejecutarse en segundo plano como si **finalizar** se hizo clic (`TRUE`).|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parámetros de contexto para iniciar asistentes](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
---
title: Parámetros de contexto | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: b69aa04583186e20df77f13f54499448b36eb29c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902624"
---
# <a name="context-parameters"></a>Parámetros de contexto
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), puede agregar asistentes a la **nuevo proyecto**, **Agregar nuevo elemento**, o **agregar subproyecto** cuadros de diálogo. Están disponibles en los asistentes que se ha agregado el **archivo** menú o con el botón secundario en un proyecto de **el Explorador de soluciones**. El IDE pasa los parámetros de contexto para la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama el asistente.  
  
 Inicie el IDE de asistentes estableciendo el <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca en la llamada del IDE a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método para el proyecto. Cuando se establece, el proyecto debe hacer que el `IVsExtensibility::RunWizardFile` método que se ejecutará con el nombre del asistente registrado o GUID y otros parámetros de contexto que el IDE le pasa.  
  
## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto  
  
| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardNewProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto. |
| `LocalDirectory` | Ubicación local de archivos de proyecto de trabajo. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `FExclusive` | Marca booleana que indica que el proyecto debe cerrar soluciones que estén abiertas. |
| `SolutionName` | Nombre del archivo de solución sin la parte del directorio o el *.sln* extensión. El *.suo* también se crea con el nombre de archivo `SolutionName`. Si este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si este nombre es una cadena vacía, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`). |
  
## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento  
  
| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddItem>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto. |
| `ProjectItems` | Ubicación local que contiene los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el *.vsdir* archivo. El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`). |
  
## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para agregar el proyecto de Sub  
  
| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Registra el tipo de asistente (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o el GUID que indica el tipo de asistente. En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación, el GUID para el asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Una cadena que es el único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nombre del proyecto. |
| `ProjectItems` | Puntero a la `ProjectItems` colección en el que funciona el asistente. Este puntero se pasa al Asistente basándose en la selección de jerarquía del proyecto. Un usuario normalmente selecciona una carpeta en la que se va a colocar el elemento y, a continuación, llama el proyecto **Agregar elemento** cuadro de diálogo. |
| `LocalDirectory` | Ubicación local de archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe desde la **agregar elementos** cuadro de diálogo. El nombre se basa en las marcas que se establecen en el *.vsdir* archivo. El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalación. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si **finalizar** se hizo clic (`TRUE`). |
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de asistentes (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parámetros de contexto para iniciar asistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
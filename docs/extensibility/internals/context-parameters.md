---
title: Parámetros de contexto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709312"
---
# <a name="context-parameters"></a>Parámetros de contexto
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE), puede agregar asistentes a los cuadros de diálogo **Nuevo proyecto**, **Agregar nuevo elemento**o Agregar **subproyecto.** Los asistentes agregados están disponibles en el menú **Archivo** o haciendo clic con el botón derecho en un proyecto en el **Explorador**de soluciones . El IDE pasa parámetros de contexto a la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama al asistente.

 El IDE inicia los <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> asistentes estableciendo la marca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> en la llamada del IDE al método para el proyecto. Cuando se establece, el `IVsExtensibility::RunWizardFile` proyecto debe hacer que el método se ejecute mediante el nombre del asistente registrado o GUID y otros parámetros de contexto que el IDE le pasa.

## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de<xref:EnvDTE.Constants.vsWizardNewProject>asistente registrado ( ) o el GUID que indica el tipo de asistente. En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la implementación, el GUID del asistente es .0F90E1D0-4999-11D1-B6D1-00A0C90F2744. |
| `ProjectName` | Cadena que es [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el nombre único del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `InstallationDirectory` | Ruta de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] acceso de directorio de la instalación es. |
| `FExclusive` | Indicador booleano que indica que el proyecto debe cerrar soluciones abiertas. |
| `SolutionName` | Nombre del archivo de solución sin la parte del directorio o la extensión *.sln.* El nombre de archivo *.suo* también se crea mediante `SolutionName`. Cuando este argumento no es una <xref:EnvDTE._Solution.Create%2A> cadena vacía, <xref:EnvDTE._Solution.AddFromTemplate%2A>el asistente lo usa antes de agregar el proyecto con . Si este nombre es una <xref:EnvDTE._Solution.AddFromTemplate%2A> cadena <xref:EnvDTE._Solution.Create%2A>vacía, utilice sin llamar a . |
| `Silent` | Booleano que indica si el asistente **Finish** debe ejecutarse`TRUE`silenciosamente como si se hiciera clic en Finalizar ( ). |

## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para Agregar nuevo elemento

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de<xref:EnvDTE.Constants.vsWizardAddItem>asistente registrado ( ) o el GUID que indica el tipo de asistente. En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la implementación, el GUID para el asistente es .0F90E1D1-4999-11D1-B6D1-00A0C90F2744. |
| `ProjectName` | Cadena que es [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el nombre único del proyecto. |
| `ProjectItems` | Ubicación local que contiene archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos.** El nombre se basa en las marcas que se establecen en el archivo *.vsdir.* El nombre puede ser un valor nulo. |
| `InstallationDirectory` | Ruta de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] acceso de directorio de la instalación es. |
| `Silent` | Booleano que indica si el asistente **Finish** debe ejecutarse`TRUE`silenciosamente como si se hiciera clic en Finalizar ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para Agregar subproyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de<xref:EnvDTE.Constants.vsWizardAddSubProject>asistente registrado ( ) o el GUID que indica el tipo de asistente. En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] la implementación, el GUID para el asistente es .0F90E1D2-4999-11D1-B6D1-00A0C90F2744. |
| `ProjectName` | Cadena que es [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el nombre único del proyecto. |
| `ProjectItems` | Puntero a `ProjectItems` la colección en la que opera el asistente. Este puntero se pasa al asistente en función de la selección de jerarquía del proyecto. Normalmente, un usuario selecciona una carpeta en la que colocar el elemento y, a continuación, llama al cuadro de diálogo **Agregar elemento** del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos.** El nombre se basa en las marcas que se establecen en el archivo *.vsdir.* El nombre puede ser un valor nulo. |
| `InstallationDirectory` | Ruta de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] acceso del directorio de la instalación. |
| `Silent` | Booleano que indica si el asistente **Finish** debe ejecutarse`TRUE`silenciosamente como si se hiciera clic en Finalizar ( ). |

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parámetros de contexto para iniciar asistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)

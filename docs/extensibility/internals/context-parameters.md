---
title: Parámetros de contexto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709312"
---
# <a name="context-parameters"></a>Parámetros de contexto
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE), puede agregar asistentes a los cuadros de diálogo **nuevo proyecto**, **Agregar nuevo elemento**o **Agregar subproyecto** . Los asistentes agregados están disponibles en el menú **archivo** o haciendo clic con el botón secundario en un proyecto de **Explorador de soluciones**. El IDE pasa los parámetros de contexto a la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama al asistente.

 El IDE inicia los asistentes estableciendo la <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca en la llamada del IDE al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método para el proyecto. Cuando se establece, el proyecto debe hacer que el `IVsExtensibility::RunWizardFile` método se ejecute utilizando el nombre del asistente registrado o el GUID y otros parámetros de contexto que el IDE le pase.

## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardNewProject> ) o GUID que indica el tipo de asistente. En la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación de, el GUID del asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalación de. |
| `FExclusive` | Marca booleana que indica que el proyecto debe cerrar soluciones abiertas. |
| `SolutionName` | Nombre del archivo de solución sin la parte del directorio o la extensión *. sln* . El nombre de archivo *. suo* también se crea mediante `SolutionName` . Cuando este argumento no es una cadena vacía, el asistente utiliza <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A> . Si este nombre es una cadena vacía, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardAddItem> ) o GUID que indica el tipo de asistente. En la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación de, el GUID del asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto. |
| `ProjectItems` | Ubicación local que contiene los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos** . El nombre se basa en las marcas que se establecen en el archivo *. vsdir* . El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalación de. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para agregar subproyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) o GUID que indica el tipo de asistente. En la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementación de, el GUID del asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto. |
| `ProjectItems` | Puntero a la `ProjectItems` colección en la que funciona el asistente. Este puntero se pasa al asistente en función de la selección de jerarquía del proyecto. Un usuario suele seleccionar una carpeta en la que colocar el elemento y, a continuación, llama al cuadro de diálogo **Agregar elemento** del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos** . El nombre se basa en las marcas que se establecen en el archivo *. vsdir* . El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso del directorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalación. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** ( `TRUE` ). |

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo del asistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parámetros de contexto para iniciar asistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)

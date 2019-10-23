---
title: Parámetros de contexto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727555"
---
# <a name="context-parameters"></a>Parámetros de contexto
En el entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede agregar asistentes a los cuadros de diálogo **nuevo proyecto**, **Agregar nuevo elemento**o **Agregar subproyecto** . Los asistentes agregados están disponibles en el menú **archivo** o haciendo clic con el botón secundario en un proyecto de **Explorador de soluciones**. El IDE pasa los parámetros de contexto a la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama al asistente.

 El IDE inicia los asistentes estableciendo el <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca en la llamada del IDE al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> para el proyecto. Cuando se establece, el proyecto debe hacer que el método `IVsExtensibility::RunWizardFile` se ejecute utilizando el nombre del asistente registrado o el GUID y otros parámetros de contexto que el IDE le pase.

## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado (<xref:EnvDTE.Constants.vsWizardNewProject>) o GUID que indica el tipo de asistente. En la implementación de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], el GUID del asistente es {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `InstallationDirectory` | Ruta de acceso al directorio del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `FExclusive` | Marca booleana que indica que el proyecto debe cerrar soluciones abiertas. |
| `SolutionName` | Nombre del archivo de solución sin la parte del directorio o la extensión *. sln* . El nombre de archivo *. suo* también se crea con `SolutionName`. Cuando este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A>. Si este nombre es una cadena vacía, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para agregar nuevo elemento

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado (<xref:EnvDTE.Constants.vsWizardAddItem>) o GUID que indica el tipo de asistente. En la implementación de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], el GUID del asistente es {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Ubicación local que contiene los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos** . El nombre se basa en las marcas que se establecen en el archivo *. vsdir* . El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso al directorio del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para agregar subproyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado (<xref:EnvDTE.Constants.vsWizardAddSubProject>) o GUID que indica el tipo de asistente. En la implementación de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], el GUID del asistente es {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único del proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `ProjectItems` | Puntero a la colección de `ProjectItems` en la que funciona el asistente. Este puntero se pasa al asistente en función de la selección de jerarquía del proyecto. Un usuario suele seleccionar una carpeta en la que colocar el elemento y, a continuación, llama al cuadro de diálogo **Agregar elemento** del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escribe en el cuadro de diálogo **Agregar elementos** . El nombre se basa en las marcas que se establecen en el archivo *. vsdir* . El nombre puede ser un valor null. |
| `InstallationDirectory` | Ruta de acceso del directorio de la instalación de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `Silent` | Valor booleano que indica si el asistente se debe ejecutar en modo silencioso como si se hubiera hecho clic en **Finalizar** (`TRUE`). |

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo del asistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parámetros de contexto para iniciar asistentes](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
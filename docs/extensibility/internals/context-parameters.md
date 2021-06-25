---
title: Parámetros de contexto | Microsoft Docs
description: Obtenga información sobre los parámetros de contexto Visual Studio entorno de desarrollo integrado (IDE) que definen el estado de un proyecto al agregar o implementar un asistente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 536e5abf92884c5c19399e73b4e1773e66919657
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898232"
---
# <a name="context-parameters"></a>Parámetros de contexto
En el entorno de desarrollo integrado (IDE), puede agregar asistentes a los cuadros de diálogo Nuevo proyecto, Agregar nuevo elemento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o Agregar subproy **proyecto.**   Los asistentes agregados están disponibles en el **menú** Archivo o haciendo clic con el botón derecho en un **proyecto Explorador de soluciones**. El IDE pasa parámetros de contexto a la implementación del asistente. Los parámetros de contexto definen el estado del proyecto cuando el IDE llama al asistente.

 El IDE inicia los asistentes estableciendo la marca en la llamada <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> del IDE al método para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> proyecto. Cuando se establece, el proyecto debe hacer que el método se ejecute mediante el nombre del asistente registrado o guid y otros parámetros de contexto que el `IVsExtensibility::RunWizardFile` IDE le pase.

## <a name="context-parameters-for-new-project"></a>Parámetros de contexto para el nuevo proyecto

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardNewProject> ) o guid que indica el tipo de asistente. En la implementación, el GUID del asistente es [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `InstallationDirectory` | Ruta de acceso del directorio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `FExclusive` | Marca booleana que indica que el proyecto debe cerrar las soluciones abiertas. |
| `SolutionName` | Nombre del archivo de solución sin la parte del directorio o la *extensión .sln.* El *nombre de archivo .suo* también se crea mediante `SolutionName` . Cuando este argumento no es una cadena vacía, el asistente usa <xref:EnvDTE._Solution.Create%2A> antes de agregar el proyecto con <xref:EnvDTE._Solution.AddFromTemplate%2A> . Si este nombre es una cadena vacía, use <xref:EnvDTE._Solution.AddFromTemplate%2A> sin llamar a <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Valor booleano que indica si el asistente debe ejecutarse en modo silencioso como **si** se hubiera hecho clic en Finalizar ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Parámetros de contexto para Agregar nuevo elemento

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardAddItem> ) o guid que indica el tipo de asistente. En la implementación, el GUID del asistente es [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del proyecto. |
| `ProjectItems` | Ubicación local que contiene archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escriba en el **cuadro de diálogo Agregar** elementos . El nombre se basa en las marcas que se establecen en el *archivo .vsdir.* El nombre puede ser un valor NULL. |
| `InstallationDirectory` | Ruta de acceso del directorio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es la instalación. |
| `Silent` | Valor booleano que indica si el asistente debe ejecutarse en modo silencioso como **si** se hubiera hecho clic en Finalizar ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Parámetros de contexto para Add Sub Project

| Parámetro | Descripción |
|-------------------------| - |
| `WizardType` | Tipo de asistente registrado ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) o guid que indica el tipo de asistente. En la implementación, el GUID del asistente es [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Cadena que es el nombre único [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del proyecto. |
| `ProjectItems` | Puntero a la `ProjectItems` colección en la que funciona el asistente. Este puntero se pasa al asistente en función de la selección de la jerarquía del proyecto. Normalmente, un usuario selecciona una carpeta en la que colocar el elemento y, a continuación, llama al cuadro de diálogo Agregar **elemento** del proyecto. |
| `LocalDirectory` | Ubicación local de los archivos de proyecto de trabajo. |
| `ItemName` | Nombre del elemento que se va a agregar. Este nombre es el nombre de archivo predeterminado o el nombre de archivo que el usuario escriba en el **cuadro de diálogo Agregar** elementos . El nombre se basa en las marcas que se establecen en el *archivo .vsdir.* El nombre puede ser un valor NULL. |
| `InstallationDirectory` | Ruta de acceso del directorio de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la instalación. |
| `Silent` | Valor booleano que indica si el asistente debe ejecutarse en modo silencioso como **si** se hubiera hecho clic en Finalizar ( `TRUE` ). |

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo del asistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parámetros de contexto para iniciar asistentes](/previous-versions/tz690efs(v=vs.140))
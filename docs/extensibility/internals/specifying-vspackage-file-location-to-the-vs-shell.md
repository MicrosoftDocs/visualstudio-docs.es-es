---
title: Especificar la ubicación del archivo VSPackage en el shell de VS | Microsoft Docs
description: Obtenga información sobre cómo puede hacer que Visual Studio busque el archivo DLL de ensamblado para cargar el VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e59bea4894d6b0014542ea2a32bf6c73bc8d797c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877863"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificación de la ubicación del archivo de VSPackage en el Shell de VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe poder localizar el archivo DLL de ensamblado para cargar el VSPackage. Puede localizarlo de varias maneras, como se describe en la tabla siguiente.

| Método | Descripción |
| - | - |
| Use la clave del registro codebase. | La clave codebase se puede usar para indicar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a que cargue el ensamblado VSPackage desde cualquier ruta de acceso de archivo completa. El valor de la clave debe ser la ruta de acceso al archivo DLL. Esta es la mejor manera de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar el ensamblado del paquete. A veces, esta técnica se conoce como la "técnica del directorio de instalación de base de código privada". Durante el registro, el valor del código base se pasa a las clases de atributo de registro a través de una instancia del <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo. |
| Coloque el archivo DLL en el directorio **PrivateAssemblies** | Coloque el ensamblado en el subdirectorio **PrivateAssemblies** del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directorio. Los ensamblados que se encuentran en **PrivateAssemblies** se detectan automáticamente, pero no están visibles en el cuadro de diálogo **Agregar referencias** . La diferencia entre **PrivateAssemblies** y **PublicAssemblies** es que los ensamblados de **PublicAssemblies** se enumeran en el cuadro de diálogo **Agregar referencias** . Si decidió no usar la técnica "directorio de instalación de codebase/privado", debe instalar en el directorio **PrivateAssemblies** |
| Usar un ensamblado con nombre seguro y la clave del registro de ensamblado. | La clave de ensamblado se puede usar para dirigir explícitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a la carga de un ensamblado de VSPackage con nombre seguro. El valor de la clave debe ser el nombre seguro del ensamblado. |
| Coloque el archivo DLL en el directorio **PublicAssemblies** | Por último, el ensamblado también se puede colocar en el subdirectorio **PublicAssemblies** Los ensamblados que se encuentran en **PublicAssemblies** se detectan automáticamente y también aparecerán en el cuadro de diálogo **Agregar referencias** en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Los ensamblados de VSPackage solo deben colocarse en el directorio **PublicAssemblies** si contienen componentes administrados que están diseñados para ser reutilizados por otros desarrolladores de VSPackage. La mayoría de los ensamblados no cumple este criterio. |

> [!NOTE]
> Use ensamblados con nombre seguro y firmados para todos los ensamblados dependientes. Estos ensamblados también deben instalarse en su propio directorio o en la caché de ensamblados global (GAC). Esto protege frente a conflictos con ensamblados que tienen el mismo nombre de archivo base, conocido como enlace de nombre seguro.

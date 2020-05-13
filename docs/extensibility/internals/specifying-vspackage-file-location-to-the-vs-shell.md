---
title: Especificación de la ubicación del archivo de VSPackage en el shell de VS ? Microsoft Docs
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
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704977"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificación de la ubicación del archivo de VSPackage en el Shell de VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debe ser capaz de localizar el archivo DLL de ensamblado para cargar el VSPackage. Puede localizarlo de varias maneras, como se describe en la tabla siguiente.

| Método | Descripción |
| - | - |
| Utilice la clave del Registro CodeBase. | La clave CodeBase se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede usar para dirigir para cargar el ensamblado de VSPackage desde cualquier ruta de acceso de archivo completa. El valor de la clave debe ser la ruta de acceso del archivo al archivo DLL. Esta es la mejor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manera de cargar el ensamblado del paquete. Esta técnica se conoce a veces como la "técnica de directorio de instalación privada/CodeBase." Durante el registro, el valor del código base se pasa <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> a las clases de atributo de registro a través de una instancia del tipo. |
| Coloque el archivo DLL en el directorio **PrivateAssemblies.** | Coloque el ensamblado en el subdirectorio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **PrivateAssemblies** del directorio. Los ensamblados ubicados en **PrivateAssemblies** se detectan automáticamente, pero no están visibles en el cuadro de diálogo **Agregar referencias.** La diferencia entre **PrivateAssemblies** y **PublicAssemblies** es que los ensamblados de **PublicAssemblies** se enumeran en el cuadro de diálogo **Agregar referencias.** Si decide no utilizar la técnica "CodeBase/private installation directory", debe instalar en el directorio **PrivateAssemblies.** |
| Use un ensamblado con nombre seguro y la clave del Registro de ensamblados. | La clave de ensamblado se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede usar para dirigir explícitamente para cargar un ensamblado VSPackage con nombre seguro. El valor de la clave debe ser el nombre seguro del ensamblado. |
| Coloque el archivo DLL en el directorio **PublicAssemblies.** | Por último, el ensamblado también se puede colocar en el **PublicAssemblies** subdirectorio. Los ensamblados ubicados en **PublicAssemblies** se detectan automáticamente y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]también aparecerán en el cuadro de diálogo Agregar **referencias** en .<br /><br /> Los ensamblados de VSPackage solo deben colocarse en el directorio **PublicAssemblies** si contienen componentes administrados destinados a ser reutilizados por otros desarrolladores de VSPackage. La mayoría de las asambleas no cumplen este criterio. |

> [!NOTE]
> Use ensamblados firmados con nombre seguro para todos los ensamblados dependientes. Estos ensamblados también deben instalarse en su propio directorio o en la caché global de ensamblados (GAC). Esto protege contra conflictos con ensamblados que tienen el mismo nombre de archivo base, conocido como enlace de nombre débil.

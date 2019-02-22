---
title: Especificar la ubicación del archivo de paquete VSPackage en el Shell de VS | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47f95231c0c7bb955271203792bdd795772b50c1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612379"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificación de la ubicación del archivo de VSPackage en el Shell de VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe ser capaz de encontrar la DLL para cargar el VSPackage del ensamblado. Puede encontrarlo de varias maneras, como se describe en la tabla siguiente.


| Método | Descripción |
| - | - |
| Use la clave del registro de base de código. | La clave de la base de código puede utilizarse para dirigir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar el ensamblado de VSPackage desde cualquier ruta de acceso completa del archivo. El valor de la clave debe ser la ruta de acceso al archivo DLL. Esta es la mejor manera de tener [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el ensamblado del paquete. Esta técnica se conoce a veces como "código base y privada instalación directory técnica." Durante el registro se pasa el valor del código base para las clases de atributos de registro a través de una instancia de la <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo. |
| Colocar el archivo DLL en el **PrivateAssemblies** directory. | Coloque el ensamblado en el **PrivateAssemblies** subdirectorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Los ensamblados se encuentran en **PrivateAssemblies** se detectan automáticamente, pero no son visibles en el **agregar referencias** cuadro de diálogo. La diferencia entre **PrivateAssemblies** y **PublicAssemblies** es que los ensamblados en **PublicAssemblies** se enumeran en la **agregar referencias**  cuadro de diálogo. Si decide no usar la técnica de "directorio de instalación de la base de código y privada" y, después, debe instalar en el **PrivateAssemblies** directory. |
| Use un ensamblado con nombre seguro y la clave del registro de ensamblado. | La clave de ensamblado se puede usar para dirigir explícitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar una fuerte con el nombre de ensamblado de VSPackage. El valor de la clave debe ser el nombre seguro del ensamblado. |
| Colocar el archivo DLL en el **PublicAssemblies** directory. | Por último, el ensamblado también se puede colocar en el **PublicAssemblies** subdirectorio. Los ensamblados se encuentran en **PublicAssemblies** se detectan automáticamente y también aparecerá en el **agregar referencias** cuadro de diálogo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Solo se deben colocar los ensamblados de VSPackage en el **PublicAssemblies** directorio si contienen los componentes que están diseñados para ser reutilizada por otros desarrolladores VSPackage administrados. La mayoría de los ensamblados no cumplen este criterio. |

> [!NOTE]
>  Usar ensamblados con nombre seguro, con signo para todos los ensamblados dependientes. Estos ensamblados también deben instalarse en su propio directorio o en la caché global de ensamblados (GAC). Esto protege contra entra en conflicto con los ensamblados que tienen el mismo nombre de archivo base, conocido como el enlace de nombre de débil.
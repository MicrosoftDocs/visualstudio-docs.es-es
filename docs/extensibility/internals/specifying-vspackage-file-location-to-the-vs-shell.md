---
title: Especificar la ubicación del archivo de paquete de VS en el Shell de VS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a4270fbd723e6c5aa6f16066066e0ca4ac74e5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132007"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificar la ubicación del archivo de paquete de VS en el Shell de VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe ser capaz de encontrar la DLL para cargar el VSPackage del ensamblado. Puede encontrarlo de varias maneras, como se describe en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|Utilice la clave del registro de código base.|La clave de código base puede utilizarse para dirigir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar el ensamblado de VSPackage desde cualquier ruta de acceso completa del archivo. El valor de la clave debe ser la ruta de acceso al archivo DLL. Se trata de la mejor manera de tener [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el ensamblado de paquete. Esta técnica se conoce a veces como la "técnica de directorio de código base y privada instalación". Durante el registro se pasa el valor del código base para las clases de atributos de registro a través de una instancia de la <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Coloque el archivo DLL en el **PrivateAssemblies** directory.|Coloque el ensamblado en el **PrivateAssemblies** subdirectorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Ensamblados que se encuentran en **PrivateAssemblies** se detectan automáticamente, pero no son visibles en el **agregar referencias** cuadro de diálogo. La diferencia entre **PrivateAssemblies** y **PublicAssemblies** es que los ensamblados en **PublicAssemblies** se enumeran en la **agregar referencias**  cuadro de diálogo. Si decide no usar la técnica de "directorio de instalación de código base y privada", debe instalar en el **PrivateAssemblies** directory.|  
|Usar un ensamblado con nombre seguro y la clave de registro del ensamblado.|La clave de ensamblado puede utilizarse para dirigir explícitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar un seguro con el nombre de ensamblado de VSPackage. El valor de la clave debe ser el nombre seguro del ensamblado.|  
|Coloque el archivo DLL en el **PublicAssemblies** directory.|Por último, el ensamblado también se puede colocar en el **PublicAssemblies** subdirectorio. Ensamblados que se encuentran en **PublicAssemblies** se detectan automáticamente y también aparecerá en la **agregar referencias** cuadro de diálogo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Ensamblados de VSPackage solo deben colocarse en el **PublicAssemblies** directorio si contienen los componentes que están diseñados para ser reutilizada por otros desarrolladores de VSPackage administrados. La mayoría de los ensamblados no cumple este criterio.|  
  
> [!NOTE]
>  Utilizar ensamblados con nombre seguro, firmados para todos los ensamblados dependientes. Estos ensamblados también deben instalarse en su propio directorio o la caché de ensamblados global (GAC). Esto protege contra entra en conflicto con los ensamblados que tienen el mismo nombre de archivo base, conocido como el enlace de nombre débil.
---
title: "Especificar la ubicaci&#243;n del archivo de VSPackage del Shell de VS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages administrado, la ubicación del archivo"
  - "VSPackages, administra la ubicación del archivo de paquete"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Especificar la ubicaci&#243;n del archivo de VSPackage del Shell de VS
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe ser capaz de encontrar el archivo DLL para cargar el VSPackage del ensamblado. Puede encontrarlo en varias formas, como se describe en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|Utilice la clave del registro de base de código.|La clave del código base puede utilizarse para dirigir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para cargar el ensamblado de VSPackage desde cualquier ruta de acceso completa del archivo. El valor de la clave debe ser la ruta de acceso al archivo DLL. Se trata de la mejor manera de tener [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el ensamblado del paquete. Esta técnica se conoce a veces como "CodeBase y privada instalación directory técnica." Durante el registro se pasa el valor del código base para las clases de atributos de registro a través de una instancia de la <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Coloque el DLL en el **PrivateAssemblies** directory.|Coloque el ensamblado en el **PrivateAssemblies** subdirectorio de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Los ensamblados se encuentran en **PrivateAssemblies** se detectan automáticamente, pero no son visibles en el **Agregar referencias** cuadro de diálogo. La diferencia entre **PrivateAssemblies** y **PublicAssemblies** es que los ensamblados en **PublicAssemblies** enumerados en el **Agregar referencias** cuadro de diálogo. Si decide no usar la técnica de "directorio de instalación de base de código y privada", debe instalar en el **PrivateAssemblies** directory.|  
|Utilizar un ensamblado con nombre seguro y la clave de registro del ensamblado.|La clave de ensamblado puede utilizarse para dirigir explícitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cargar una fuerte con el nombre de ensamblado de VSPackage. El valor de la clave debe ser el nombre seguro del ensamblado.|  
|Coloque el DLL en el **PublicAssemblies** directory.|Por último, el ensamblado también se puede colocar en el **PublicAssemblies** subdirectorio. Los ensamblados se encuentran en **PublicAssemblies** se detectan automáticamente y también aparecerán en el **Agregar referencias** cuadro de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Ensamblados de VSPackage sólo deben ubicarse en el **PublicAssemblies** administra de directorio si contienen los componentes que están pensados para ser reutilizada por otros desarrolladores de VSPackage. La mayoría de los ensamblados no cumplen este criterio.|  
  
> [!NOTE]
>  Utilizar ensamblados firmados con nombre seguro para todos los ensamblados dependientes. Estos ensamblados también deben instalarse en su propio directorio o en la caché de ensamblados global \(GAC\). Esto protege contra los conflictos con los ensamblados que tengan el mismo nombre de archivo base, conocido como enlace de nombres débil.
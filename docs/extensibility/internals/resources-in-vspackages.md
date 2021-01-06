---
title: Recursos en VSPackages | Microsoft Docs
description: Obtenga información sobre qué tipos de recursos localizados se pueden incrustar en VSPackages. También puede incrustar recursos en archivos dll de la interfaz de usuario satélite nativa o en archivos dll satélite administrados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2693d25e0b175a075bcc644077895076b75b7578
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875731"
---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
Puede incrustar recursos localizados en archivos dll de la interfaz de usuario satélite nativa, archivos dll satélite administrados o en un VSPackage administrado.

 Algunos recursos no se pueden incrustar en VSPackages. Se pueden incrustar los siguientes tipos administrados:

- Cadenas

- Claves de carga de paquetes (que también son cadenas)

- Iconos de la ventana de herramientas

- Archivos de salida de tabla de comandos compilados (CTO)

- Mapas de bits CTO

- Ayuda de la línea de comandos

- Acerca de los datos del cuadro de diálogo

  Los recursos de un paquete administrado se seleccionan por el ID. de recurso. Una excepción es el archivo CTO, que se debe denominar CTMENU. El archivo CTO debe aparecer en la tabla de recursos como `byte[]` . El resto de los elementos de recursos se identifican por tipo.

  Puede usar el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atributo para indicar a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los recursos administrados que están disponibles.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>La configuración de este modo indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe omitir los archivos dll satélite no administrados al buscar recursos, por ejemplo, mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Si encuentra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dos o más recursos que tienen el mismo identificador de recurso, utiliza el primer recurso que encuentre.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente es una representación administrada de un icono de ventana de herramientas.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 En el ejemplo siguiente se muestra cómo insertar la matriz de bytes CTO, que se debe denominar CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Notas de implementación
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] retrasa la carga de VSPackages siempre que sea posible. Una consecuencia de la inserción de un archivo CTO en un VSPackage es que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe cargar todos esos VSPackages en la memoria durante la instalación, que es cuando se genera una tabla de comandos combinada. Los recursos se pueden extraer de un VSPackage mediante el examen de los metadatos sin ejecutar código en el VSPackage. En este momento, el VSPackage no se ha inicializado, por lo que la pérdida de rendimiento es mínima.

 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita un recurso de un VSPackage después de la instalación, es probable que ese paquete ya esté cargado e inicializado, por lo que la pérdida de rendimiento es mínima.

## <a name="see-also"></a>Consulte también
- [Administración de VSPackages](../../extensibility/managing-vspackages.md)
- [Recursos localizados en aplicaciones MFC: archivos DLL satélite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)

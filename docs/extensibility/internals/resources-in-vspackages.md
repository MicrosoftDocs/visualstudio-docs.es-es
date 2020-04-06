---
title: Recursos en VSPackages ? Microsoft Docs
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
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705599"
---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
Puede incrustar recursos localizados en archivos DLL de interfaz de usuario satélite nativos, archivos DLL de satélite administrados o en un VSPackage administrado.

 Algunos recursos no se pueden incrustar en VSPackages. Se pueden incrustar los siguientes tipos administrados:

- Cadenas

- Claves de carga de paquete (que también son cadenas)

- Iconos de la ventana de herramientas

- Archivos de salida de tabla de comandos compilados (CTO)

- Mapas de bits CTO

- Ayuda de la línea de comandos

- Acerca de los datos del cuadro de diálogo

  Los recursos de un paquete administrado se seleccionan por identificador de recurso. Una excepción es el archivo CTO, que debe llamarse CTMENU. El archivo CTO debe aparecer en `byte[]`la tabla de recursos como un archivo . Todos los demás elementos de recursos se identifican por tipo.

  Puede usar <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> el atributo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para indicar que los recursos administrados están disponibles.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Establecer <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de esta manera [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] indica que debe omitir los archivos DLL satélite no administrados cuando busca recursos, por ejemplo, mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encuentra dos o más recursos que tienen el mismo identificador de recurso, usa el primer recurso que encuentra.

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

 En el ejemplo siguiente se muestra cómo incrustar la matriz de bytes CTO, que debe llamarse CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]retrasa la carga de VSPackages siempre que sea posible. Una consecuencia de incrustar un archivo CTO [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en un VSPackage es que debe cargar todos estos VSPackages en memoria durante la instalación, que es cuando se compila una tabla de comandos combinada. Los recursos se pueden extraer de un VSPackage examinando los metadatos sin ejecutar código en el VSPackage. El VSPackage no se inicializa en este momento, por lo que la pérdida de rendimiento es mínima.

 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicita un recurso de un VSPackage después de la instalación, es probable que ese paquete ya esté cargado e inicializado, por lo que la pérdida de rendimiento es mínima.

## <a name="see-also"></a>Vea también
- [Administración de VSPackages](../../extensibility/managing-vspackages.md)
- [Recursos localizados en aplicaciones MFC: archivos DLL satélite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)

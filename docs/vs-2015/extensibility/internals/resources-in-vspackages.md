---
title: Recursos en VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696088"
---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
  Puede usar el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atributo para indicar a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] los recursos administrados que están disponibles.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>La configuración de este modo indica que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe omitir los archivos dll satélite no administrados al buscar recursos, por ejemplo, mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Si encuentra [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dos o más recursos que tienen el mismo identificador de recurso, utiliza el primer recurso que encuentre.  
  
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
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] retrasa la carga de VSPackages siempre que sea posible. Una consecuencia de la inserción de un archivo CTO en un VSPackage es que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe cargar todos esos VSPackages en la memoria durante la instalación, que es cuando se genera una tabla de comandos combinada. Los recursos se pueden extraer de un VSPackage mediante el examen de los metadatos sin ejecutar código en el VSPackage. En este momento, el VSPackage no se ha inicializado, por lo que la pérdida de rendimiento es mínima.  
  
 Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] solicita un recurso de un VSPackage después de la instalación, es probable que ese paquete ya esté cargado e inicializado, por lo que la pérdida de rendimiento es mínima.  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages administrado](../../misc/managed-vspackages.md)   
 [Administrar VSPackages](../../extensibility/managing-vspackages.md)   
 [Recursos localizados en aplicaciones MFC: archivos dll satélite](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackages administrado](../../misc/managed-vspackages.md)

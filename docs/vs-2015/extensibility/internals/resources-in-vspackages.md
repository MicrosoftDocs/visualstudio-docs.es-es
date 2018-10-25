---
title: Recursos de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d032863677a24f377da8068b4a6e5565c5a2241c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830683"
---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede incrustar los recursos localizados en nativo satélite DLL de interfaz de usuario, archivos DLL satélite administrados, o en un VSPackage administrado propio.  
  
 Algunos recursos no se puede incrustar en VSPackages. Los siguientes tipos administrados se pueden insertar:  
  
- Cadenas  
  
- Claves de carga de paquete (que también son cadenas)  
  
- Iconos de la ventana de herramienta  
  
- Archivos de salida de la tabla de comandos (CTO) compilados  
  
- Mapas de bits de director de tecnología  
  
- Ayuda de línea de comandos  
  
- Acerca de los datos de cuadro de diálogo  
  
  Se seleccionan los recursos en un paquete administrado por el identificador de recurso. Una excepción es el archivo de director de tecnología, que se debe denominar CTMENU. El archivo de director de tecnología debe aparecer en la tabla de recursos como un `byte[]`. Todos los demás elementos de recursos se identifican por tipo.  
  
  Puede usar el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atributo para indicar al [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que están disponibles los recursos administrados.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  Establecer <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de esta manera, indica que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe omitir los archivos DLL no administrada satélite al buscar los recursos, por ejemplo, mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] encuentra dos o más recursos que tienen el mismo identificador de recurso, usa el primer recurso busca.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente es una representación administrada de un icono de ventana de herramienta.  
  
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
  
 El ejemplo siguiente muestra cómo incrustar la matriz de bytes del director de tecnología, que se debe denominar CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] carga de retrasos de VSPackages siempre que sea posible. Una consecuencia de incrustar un archivo de director de tecnología en un VSPackage es que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe cargar todos los VSPackages de este tipo en la memoria durante la instalación, que es cuando se crea una tabla combinada de comando. Los recursos se pueden extraer de un VSPackage mediante el examen de los metadatos sin ejecutar código en el VSPackage. No se ha inicializado el VSPackage en este momento, por lo que la pérdida de rendimiento es mínima.  
  
 Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] las solicitudes de un recurso desde un VSPackage después de la instalación, es probable que se cargan y se inicializan, ya que el paquete por lo que la pérdida de rendimiento es mínima.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages administrado](../../misc/managed-vspackages.md)   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)   
 [Recursos localizados en aplicaciones MFC: archivos DLL satélite](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackages administrado](../../misc/managed-vspackages.md)


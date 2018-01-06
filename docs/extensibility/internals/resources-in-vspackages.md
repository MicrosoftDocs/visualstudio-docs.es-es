---
title: Recursos de VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee9d108e7a7a6a5bd971b20c12858edf28ac0cf3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
Puede incrustar los recursos localizados en nativo satélite DLL de interfaz de usuario, archivos DLL satélite administrados, o en un VSPackage administrado propio.  
  
 Algunos recursos no se pueden incrustar en los paquetes VSPackage. Se pueden incrustar los tipos administrados siguientes:  
  
-   Cadenas  
  
-   Claves de carga de paquete (que son cadenas)  
  
-   Iconos de la ventana de herramienta  
  
-   Archivos compilados de la salida de comando tabla (Director técnico)  
  
-   Mapas de bits de director de tecnología  
  
-   Ayuda de línea de comandos  
  
-   Acerca de los datos de cuadro de diálogo  
  
 Se seleccionan los recursos en un paquete administrado por el identificador de recurso. Una excepción es el archivo de director de tecnología, que se debe denominar CTMENU. El archivo de director de tecnología debe aparecer en la tabla de recursos como un `byte[]`. Todos los demás elementos de recurso se identifican por tipo.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atributo para indicar al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que están disponibles los recursos administrados.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Establecer <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> de esta manera, indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe omitir los archivos DLL no administrada satélite cuando busca recursos, por ejemplo, mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encuentra dos o más recursos que tienen el mismo identificador de recurso, utiliza el primer recurso busca.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente es una representación administrada de un icono de ventana de herramienta.  
  
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
  
 En el ejemplo siguiente se muestra cómo incrustar la matriz de bytes de director de tecnología, que se debe denominar CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carga de retrasos de VSPackages siempre que sea posible. Una consecuencia de incrustar un archivo de director de tecnología en un paquete VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe cargar este tipo de paquetes VSPackage en la memoria durante la instalación, que es cuando se crea una tabla de comandos fusionada. Los recursos se pueden extraer un paquete VSPackage mediante el examen de los metadatos sin ejecutar código en el VSPackage. No se inicializó el VSPackage en este momento, por lo que la pérdida de rendimiento es mínimo.  
  
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las solicitudes de un recurso desde un VSPackage después de la instalación, es probable que ya se han cargado e inicializado, ese paquete por lo que la pérdida de rendimiento es mínimo.  
  
## <a name="see-also"></a>Vea también  
 [Administrar paquetes VSPackage](../../extensibility/managing-vspackages.md)   
 [Recursos localizados en aplicaciones MFC: archivos DLL satélite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   

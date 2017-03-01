---
title: Recursos de VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Recursos de VSPackages
Puede incrustar recursos localizados en nativo UI archivos DLL satélite, archivos DLL satélite administrados, o en un VSPackage administrado propio.  
  
 Algunos recursos no se pueden incrustar en VSPackages. Se pueden incrustar los siguientes tipos administrados:  
  
-   Cadenas  
  
-   Claves de carga de paquete (que también son cadenas)  
  
-   Iconos de la ventana de herramienta  
  
-   Archivos compilados de la salida de la tabla de comandos (CTO)  
  
-   Mapas de bits de director de tecnología  
  
-   Ayuda de línea de comandos  
  
-   Acerca de los datos de cuadro de diálogo  
  
 Se seleccionan los recursos en un paquete administrado por el identificador de recurso. Una excepción es el archivo CTO, que se debe denominar CTMENU. El archivo CTO debe aparecer en la tabla de recursos como un `byte[]`. Todos los demás elementos de recursos se identifican por tipo.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>atributo para indicar al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que están disponibles los recursos administrados.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[VSSDKResources&#1;](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources n.º&1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Configuración de <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>de esta manera, indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe omitir los archivos DLL no administrada satélite cuando busca recursos, por ejemplo, mediante el uso de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encuentra dos o más recursos que tienen el mismo identificador de recurso, utiliza el primer recurso que se encuentra.  
  
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
  
 En el ejemplo siguiente se muestra cómo incrustar la matriz de bytes CTO, que se debe denominar CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carga de retrasos de VSPackages siempre que sea posible. Es una consecuencia de incrustar un archivo CTO en un VSPackage que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe cargar este tipo VSPackages en memoria durante la instalación, que es cuando se crea una tabla combinada de comando. Los recursos se pueden extraer un paquete VSPackage examinando los metadatos sin ejecutar código en el paquete VSPackage. El VSPackage no se inicializa en este momento, por lo que la pérdida de rendimiento es mínima.  
  
 Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicitudes de un recurso de un VSPackage después de la instalación, es probable que se cargan y se inicializan, ya que el paquete para la pérdida de rendimiento es mínima.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages administrado](../../misc/managed-vspackages.md)   
 [Administración de VSPackages](../../extensibility/managing-vspackages.md)   
 [Recursos localizados en aplicaciones MFC: archivos DLL satélite](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [VSPackages administrado](../../misc/managed-vspackages.md)

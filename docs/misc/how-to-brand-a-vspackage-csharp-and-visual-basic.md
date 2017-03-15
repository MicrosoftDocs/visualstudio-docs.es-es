---
title: "C&#243;mo: Personalizar la marca de un paquete VSPackage (C# y Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo Acerca de"
  - "VSPackages, pantallas de presentación"
  - "VSPackages, personalización de marca"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# C&#243;mo: Personalizar la marca de un paquete VSPackage (C# y Visual Basic)
Aparezcan en el cuadro de diálogo de **Acerca de** y la pantalla de presentación, VSPackages debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> .  esto proporciona la siguiente información a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Name  
  
-   Identificador, como serie o número de versión  
  
-   Información  
  
-   Icono de logotipo  
  
 el código siguiente es de [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
### para implementar la interfaz de IVsInstalledProduct  
  
1.  Agregue el atributo de <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> a la clase que implementa el paquete VSPackage.  Esta clase debe derivarse de <xref:Microsoft.VisualStudio.Shell.Package> y de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     El primer argumento, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>, atributo de <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> indica a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que utilice <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> para obtener información de producto, en lugar de la clave del Registro de InstalledProducts.  Los argumentos que seleccione a recursos de cadena para mostrar el nombre de producto, los detalles, y el identificador, respectivamente.  Sin embargo, como el primer argumento es `true`, los argumentos restantes son `null`.  
  
2.  Haga clic con el botón secundario en <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, elija **Implementar interfaz**, y haga clic en **Implementar interfaz**.  
  
3.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> utilizando el código siguiente.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llama a estos métodos para obtener información para calificar el paquete VSPackage.  El método de GetResourceString se utiliza para buscar esta información.  
  
    > [!NOTE]
    >  Los comentarios de código se eliminan para la brevedad.  Puede encontrarlos en [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
### Para mantener las cadenas de la información del producto  
  
1.  Haga doble clic en el archivo de recursos .resx asociado al Paquete.  
  
     El editor de recursos se abrirá.  
  
2.  Buscar o agregue el nombre del producto, la información, como el identificador  
  
     las cadenas de recursos siguientes son de [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
     @101  
     Pantalla de presentación del paquete y nombre About Official de Ayuda \(C\#\).  
  
     @102  
     Este paquete muestra cómo mostrar el texto y la imagen de la pantalla de presentación y la ayuda sobre.  
  
     @104  
     8.0  
  
3.  Seleccione y editar esta información como desee.  
  
### Para mantener los iconos y mapas de bits del producto  
  
1.  Agregue los mapas de bits y los iconos al proyecto como recursos del proyecto.  
  
     Para obtener más información, vea [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/es-es/95f15d03-bed0-410c-8d1f-dece5199ba1e).  
  
2.  Cierre el editor de recursos y vuelva a abrir el archivo .resx en XML o un editor de texto.  
  
    > [!NOTE]
    >  El editor de recursos no admite id. de recurso a los elementos que no son cadenas.  
  
3.  Buscar o agregue el icono y trace una correspondencia de bits los recursos en el archivo .resx.  Los siguientes recursos son de [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### Para probar el cuadro de diálogo y muestra de presentación Acerca de  
  
-   Para probar el Paquete, vea [Cómo: probar la pantalla Ayuda \- Acerca de y la pantalla de presentación](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Vea también  
 [Personalización de marca de VSPackage](../misc/vspackage-branding.md)
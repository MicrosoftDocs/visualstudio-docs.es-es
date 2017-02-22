---
title: "Tutorial: Agregar XAML personalizado a la p&#225;gina de inicio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "página principal personalizada"
  - "página de inicio de XAML"
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Agregar XAML personalizado a la p&#225;gina de inicio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial muestra cómo crear una Visual Studio página principal personalizada que contiene un explorador Web.  
  
## Agregar XAML personalizado  
  
1.  Crear una página de inicio siguiendo las instrucciones en [Crear una página principal personalizada](../extensibility/creating-a-custom-start-page.md).  
  
2.  En el archivo MainWindow.xaml, busque la sección \< Grid \>.  
  
3.  Agregue un elemento \< TabControl \> y \< TabItem \> dentro del elemento \< Grid \>, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Grid> <TabControl> <TabItem Header="Bing" Height="Auto"> <Frame Source="http://www.bing.com" /> </TabItem> </TabControl> </Grid>  
    ```  
  
4.  Agregue a un segundo \< TabItem \> con un elemento \< Button \> que abre un nuevo proyecto:  
  
    ```xml  
    <Grid> <TabControl> <TabItem Header="MyButton" Height="Auto"> <Button Name="btnNewProj" Content="New Project" Command="{x:Static vscom:VSCommands.ExecuteCommand}" CommandParameter="File.NewProject" > </Button> </TabItem> <TabItem Header="Bing" Height="Auto"> <Frame Source="http://www.bing.com" /> </TabItem> </TabControl> </Grid>  
    ```  
  
## Probar la página principal personalizada  
  
1.  Presione F5.  
  
     Se abre la instancia experimental de Visual Studio con la página de inicio personalizado instalado pero no se ha seleccionado.  
  
2.  En la instancia experimental de Visual Studio, abra el **\/Options herramientas \/ entorno** página.  
  
3.  Seleccione **Inicio**. En el **Personalizar página principal** lista, seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
4.  En el **vista** menú, haga clic en **página de inicio**.  
  
5.  Haga clic en el **Bing** ficha.  
  
     Debería ver una página web de Bing.  
  
6.  Haga clic en el **Mi botón** ficha.  
  
     Debería ver un **MyProject** botón que abre el **nuevo proyecto** cuadro de diálogo.  
  
7.  Cierre la instancia experimental.  
  
## Aplicar la página principal personalizada  
  
#### Para probar la página de inicio personalizado  
  
1.  En **Herramientas \/ Opciones \/ entorno**, seleccione **Inicio**. En el **Personalizar página principal** lista, seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
## Pasos siguientes  
 La página de inicio de Visual Studio ahora contiene una pestaña que muestra una pestaña de explorador Web y una ficha de Mi botón. Puede crear páginas principales personalizadas que tengan otra funcionalidad utilizando el *código subyacente* modelo para agregar un archivo .dll personalizado, como se muestra en [Agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir páginas principales personalizadas con otros usuarios publicando el archivo .vsix resultante a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web o a otro sitio Web o red compartir. Para obtener más información, consulta [Implementar páginas de inicio personalizado](../extensibility/deploying-custom-start-pages.md).  
  
## Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles contenedores de WPF](http://msdn.microsoft.com/es-es/a0177167-d7db-4205-9607-8ae316952566)
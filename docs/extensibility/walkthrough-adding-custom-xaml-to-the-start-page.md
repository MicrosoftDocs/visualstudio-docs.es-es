---
title: "Tutorial: Agregar XAML personalizado a la página de inicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 924a6e2640002bc47eb75c903c46b5a170a9c308
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Tutorial: Agregar XAML personalizado a la página de inicio
Este tutorial muestra cómo crear un Visual Studio página de inicio personalizada que contiene un explorador Web.  
  
## <a name="adding-custom-xaml"></a>Agregar XAML personalizado  
  
1.  Cree una página de inicio siguiendo las instrucciones de [crear una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).  
  
2.  En el archivo MainWindow.xaml, busque el \<cuadrícula > sección.  
  
3.  Agregar un \<TabControl > elemento y un \<TabItem > dentro de la \< cuadrícula > elemento, tal como se muestra en el ejemplo siguiente.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Agregue un segundo \<TabItem >, con un \<botón > elemento que se abre un nuevo proyecto:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Probar la página de inicio personalizada  
  
1.  Presione F5.  
  
     Se abre la instancia experimental de Visual Studio, con la página de inicio personalizada instalada pero no se ha seleccionado.  
  
2.  En la instancia experimental de Visual Studio, abra el **herramientas/opciones / entorno** página.  
  
3.  Seleccione **inicio**. En el **Personalizar página principal** lista, seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
4.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
5.  Haga clic en el **Bing** ficha.  
  
     Debería ver una página web de Bing.  
  
6.  Haga clic en el **Mi botón** ficha.  
  
     Debería ver un **MyProject** botón que abre el **nuevo proyecto** cuadro de diálogo.  
  
7.  Cierre la instancia experimental.  
  
## <a name="applying-the-custom-start-page"></a>Aplicación de la página de inicio personalizada  
  
#### <a name="to-test-the-custom-start-page"></a>Para probar la página de inicio personalizada  
  
1.  En **herramientas / opciones / entorno**, seleccione **inicio**. En el **Personalizar página principal** lista, seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 La página de inicio de Visual Studio ahora contiene una pestaña que muestra una pestaña del explorador Web y una pestaña de Mi botón. Puede crear páginas de inicio personalizadas que tengan otra funcionalidad utilizando la *código subyacente* modelo para agregar un archivo .dll personalizado, como se muestra en [agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir las páginas de inicio personalizado con otros usuarios al publicar el archivo .vsix resultante para la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web o a otro sitio Web o red compartir. Para obtener más información, consulte [implementar las páginas de inicio personalizada](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles de contenedor WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
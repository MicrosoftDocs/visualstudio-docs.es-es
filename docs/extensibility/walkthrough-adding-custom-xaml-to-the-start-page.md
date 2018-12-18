---
title: 'Tutorial: Agregar XAML personalizado a la página de inicio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0b6d095ad9fb45d5cc9bd8979a267cb2ccf961f
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495627"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Tutorial: Agregar XAML personalizado a la página de inicio
Este tutorial muestra cómo crear un Visual Studio página de inicio personalizada que contiene un explorador Web.  
  
## <a name="adding-custom-xaml"></a>Adición de XAML personalizado  
  
1.  Cree una página de inicio siguiendo las instrucciones de [crear una página principal personalizada](../extensibility/creating-a-custom-start-page.md).  
  
2.  En el *MainWindow.xaml* de archivos, busque el \<cuadrícula > sección.  
  
3.  Agregar un \<TabControl > elemento y un \<TabItem > dentro de la \< cuadrícula > elemento, como se muestra en el ejemplo siguiente.  
  
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
  
1.  Presione **F5**.  
  
     Se abre la instancia experimental de Visual Studio con la página de inicio personalizada instalada pero no seleccionada.  
  
2.  En la instancia experimental de Visual Studio, abra el **herramientas/opciones / entorno** página.  
  
3.  Seleccione **inicio**. En el **Personalizar página principal** lista, seleccione su *.xaml* de archivo y haga clic en **Aceptar**.  
  
4.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
5.  Haga clic en el **Bing** ficha.  
  
     Debería ver una página web de Bing.  
  
6.  Haga clic en el **MyButton** ficha.  
  
     Debería ver un **MyProject** button, que abre el **nuevo proyecto** cuadro de diálogo.  
  
7.  Cierre la instancia experimental.  
  
## <a name="apply-the-custom-start-page"></a>Se aplican a la página de inicio personalizada  
  
### <a name="to-test-the-custom-start-page"></a>Para probar la página de inicio personalizada  
  
1.  En **herramientas / opciones / entorno**, seleccione **inicio**. En el **Personalizar página principal** lista, seleccione su *.xaml* de archivo y haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 La página de inicio de Visual Studio ahora contiene una pestaña que muestra una pestaña del explorador Web y una pestaña MyButton. Puede crear páginas principales personalizadas que tengan otra funcionalidad mediante el *código* modelo para agregar un archivo .dll personalizado, como se muestra en [agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir páginas principales personalizadas con otros usuarios mediante la publicación del archivo .vsix resultante a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web o a otro sitio Web o red compartir. Para obtener más información, consulte [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Controles de contenedor WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
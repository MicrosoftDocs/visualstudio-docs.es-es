---
title: 'Tutorial: Adición de XAML personalizado a la página de inicio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2ee368224eb4991a2f1f167d565bd2b07f85d4c6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072181"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Tutorial: Agregar XAML personalizado a la página de inicio

Este tutorial muestra cómo crear una página de inicio personalizada de Visual Studio que contiene un explorador Web.

## <a name="add-custom-xaml"></a>Agregar XAML personalizado

1. Cree una página de inicio siguiendo las instrucciones de [crear una página principal personalizada](../extensibility/creating-a-custom-start-page.md).

2. En el *MainWindow.xaml* de archivos, busque el \<cuadrícula > sección.

3. Agregar un \<TabControl > elemento y un \<TabItem > dentro de la \< cuadrícula > elemento, como se muestra en el ejemplo siguiente.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Agregue un segundo \<TabItem >, con un \<botón > elemento que se abre un nuevo proyecto:

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

## <a name="test-the-custom-start-page"></a>Probar la página de inicio personalizada

1. Presione **F5**.

     Se abre la instancia experimental de Visual Studio con la página de inicio personalizada instalada pero no seleccionada.

2. En la instancia experimental de Visual Studio, abra el **herramientas/opciones / entorno** página.

3. Seleccione **inicio**. En el **Personalizar página principal** lista, seleccione su *.xaml* de archivo y haga clic en **Aceptar**.

4. En el menú **Vista** , haga clic en **Página de inicio**.

5. Haga clic en el **Bing** ficha.

     Debería ver una página web de Bing.

6. Haga clic en el **MyButton** ficha.

     Debería ver un **MyProject** button, que abre el **nuevo proyecto** cuadro de diálogo.

7. Cierre la instancia experimental.

Para aplicar la página de inicio personalizada, en **herramientas** > **opciones** > **entorno**, seleccione **inicio**. En el **Personalizar página principal** lista, seleccione su *.xaml* de archivo y haga clic en **Aceptar**.

## <a name="next-steps"></a>Pasos siguientes

La página de inicio de Visual Studio ahora contiene una pestaña que muestra una pestaña del explorador Web y una pestaña MyButton. Puede crear páginas de inicio personalizadas que tengan otra funcionalidad mediante el *código* modelo para agregar un archivo .dll personalizado, como se muestra en [agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir páginas de inicio personalizada con otros usuarios mediante la publicación del archivo .vsix resultante a la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web o a otro sitio Web o red compartir. Para obtener más información, consulta [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vea también

- [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controles de contenedor WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
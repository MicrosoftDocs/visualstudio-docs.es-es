---
title: 'Tutorial: agregar XAML personalizado a la página de inicio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: a13aada6cca9b54d8469885ab4c314a89cd06d6c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905965"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Tutorial: agregar XAML personalizado a la página de inicio

En este tutorial se muestra cómo crear una página de inicio personalizada de Visual Studio que contiene un explorador Web.

## <a name="add-custom-xaml"></a>Agregar XAML personalizado

1. Cree una página de inicio siguiendo las instrucciones de [creación de una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).

2. En el archivo *MainWindow. Xaml* , busque la \<Grid> sección.

3. Agregue un \<TabControl> elemento y un \<TabItem> dentro del \< Grid> elemento, como se muestra en el ejemplo siguiente.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Agregue un segundo \<TabItem> , con un \<Button> elemento que abra un nuevo proyecto:

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

     Se abre la instancia experimental de Visual Studio, con la página de inicio personalizada instalada pero no seleccionada.

2. En la instancia experimental de Visual Studio, abra la página **herramientas/Options/entorno** .

3. Seleccione **Inicio**. En la lista **Personalizar Página principal** , seleccione el archivo *. Xaml* y haga clic en **Aceptar**.

4. En el menú **Vista** , haga clic en **Página de inicio**.

5. Haga clic en la pestaña **Bing** .

     Debería ver una página web de Bing.

6. Haga clic en la pestaña **myButton** .

     Debería ver un botón de **perproject** , que abre el cuadro de diálogo **nuevo proyecto** .

7. Cierre la instancia experimental.

Para aplicar la página de inicio personalizada, en **herramientas**  >  **Opciones**  >  **entorno**, seleccione **Inicio**. En la lista **Personalizar Página principal** , seleccione el archivo *. Xaml* y haga clic en **Aceptar**.

## <a name="next-steps"></a>Pasos siguientes

La página de inicio de Visual Studio contiene ahora una pestaña que muestra una pestaña del explorador Web y una pestaña MyButton. Puede crear páginas de inicio personalizadas que tienen otras funciones mediante el uso del modelo *de código subyacente* para agregar un archivo. dll personalizado, tal como se muestra en [Agregar control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir páginas de inicio personalizadas con otros usuarios si publica el archivo. vsix resultante en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , o en otro sitio web o recurso compartido de red. Para obtener más información, consulta [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vea también

- [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controles de contenedor de WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)

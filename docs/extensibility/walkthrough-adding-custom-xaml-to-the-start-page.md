---
title: 'Tutorial: Agregar XAML personalizado a la página de inicio ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697666"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Tutorial: Agregar XAML personalizado a la página de inicio

En este tutorial se muestra cómo crear una página de inicio de Visual Studio personalizada que contiene un explorador web.

## <a name="add-custom-xaml"></a>Agregar XAML personalizado

1. Cree una página de inicio siguiendo las instrucciones de Crear una página de [inicio personalizada.](../extensibility/creating-a-custom-start-page.md)

2. En el archivo *MainWindow.xaml,* busque la \<sección Grid>.

3. Agregue \<un elemento> \<TabControl y \< un> TabItem dentro del elemento Grid>, como se muestra en el ejemplo siguiente.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Agregue un \<segundo> TabItem, con un \<elemento Button> que abra un nuevo proyecto:

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

## <a name="test-the-custom-start-page"></a>Pruebe la página de inicio personalizada

1. Presione **F5**.

     Se abre la instancia experimental de Visual Studio, con la página de inicio personalizada instalada pero no seleccionada.

2. En la instancia experimental de Visual Studio, abra la página **Herramientas /Opciones / Entorno.**

3. Seleccione **Inicio**. En la lista Personalizar página de **inicio,** seleccione el archivo *.xaml* y haga clic en **Aceptar**.

4. En el menú **Vista** , haga clic en **Página de inicio**.

5. Haga clic en la pestaña **Bing.**

     Debería ver una página web de Bing.

6. Haga clic en la pestaña **MyButton.**

     Debería ver un botón **MyProject,** que abre el cuadro de diálogo **Nuevo proyecto.**

7. Cierre la instancia experimental.

Para aplicar la página de inicio personalizada, en**Entorno**de**opciones** > de **herramientas** > , seleccione **Inicio**. En la lista Personalizar página de **inicio,** seleccione el archivo *.xaml* y haga clic en **Aceptar**.

## <a name="next-steps"></a>Pasos siguientes

La página de inicio de Visual Studio ahora contiene una pestaña que muestra una pestaña del explorador web y una pestaña MyButton. Puede crear páginas de inicio personalizadas que tengan otras funciones mediante el modelo *de código subyacente* para agregar un archivo .dll personalizado, como se muestra en Agregar control de usuario a la página de [inicio](../extensibility/adding-user-control-to-the-start-page.md). Puede compartir páginas de inicio personalizadas con otros usuarios publicando el archivo .vsix resultante en el sitio Web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o en otro sitio Web o recurso compartido de red. Para obtener más información, consulta [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vea también

- [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controles de contenedor WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)

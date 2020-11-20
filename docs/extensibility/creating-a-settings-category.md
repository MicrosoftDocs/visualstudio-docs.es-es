---
title: Crear una categoría de configuración | Microsoft Docs
description: Obtenga información sobre cómo crear una categoría de configuración de Visual Studio y usarla para guardar y restaurar valores de un archivo de configuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 468b1a44fb4754f86b31992e2c6d96bf6380592d
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974547"
---
# <a name="create-a-settings-category"></a>Crear una categoría de configuración

En este tutorial, creará una categoría de configuración de Visual Studio y la usará para guardar valores y restaurar los valores de un archivo de configuración. Una categoría de configuración es un grupo de propiedades relacionadas que aparecen como "punto de configuración personalizada". es decir, como una casilla en el Asistente para **importar y exportar configuraciones** . (Puede encontrarla en el menú **herramientas** ). La configuración se guarda o se restaura como una categoría y la configuración individual no se muestra en el asistente. Para obtener más información, vea [Configuración del entorno](../ide/environment-settings.md).

Para crear una categoría de configuración, debe derivarla de la <xref:Microsoft.VisualStudio.Shell.DialogPage> clase.

Para iniciar este tutorial, primero debe completar la primera sección de la [Página crear una opción](../extensibility/creating-an-options-page.md). La cuadrícula de propiedades opciones resultantes permite examinar y cambiar las propiedades de la categoría. Después de guardar la categoría de propiedad en un archivo de configuración, examine el archivo para ver cómo se almacenan los valores de propiedad.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Crear una categoría de configuración
 En esta sección, se usa un punto de configuración personalizado para guardar y restaurar los valores de la categoría de configuración.

### <a name="to-create-a-settings-category"></a>Para crear una categoría de configuración

1. Complete la [Página crear una opción](../extensibility/creating-an-options-page.md).

2. Abra el archivo *VSPackage. resx* y agregue estos tres recursos de cadena:

    |Nombre|Value|
    |----------|-----------|
    |106|Mi categoría|
    |107|Mi configuración|
    |108|OptionInteger y OptionFloat|

     Esto crea recursos que denominan la categoría "My Category", el objeto "My Settings" y la categoría Description "OptionInteger and OptionFloat".

    > [!NOTE]
    > De estos tres, solo el nombre de categoría no aparece en el Asistente para **importar y exportar configuraciones** .

3. En *MyToolsOptionsPackage.CS*, agregue una `float` propiedad denominada `OptionFloat` a la `OptionPageGrid` clase, tal y como se muestra en el ejemplo siguiente.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > La `OptionPageGrid` categoría denominada "My Category" ahora se compone de las dos propiedades, `OptionInteger` y `OptionFloat` .

4. Agregue un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a la `MyToolsOptionsPackage` clase y asígnele el valor de CategoryName "My Category", asígnele el nombreObjeto "My Settings" y establezca isToolsOptionPage en true. Establezca categoryResourceID, objectNameResourceID y DescriptionResourceID en los identificadores de recurso de cadena correspondientes creados anteriormente.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compile la solución y comience la depuración. En la instancia experimental, debería ver que **la página de cuadrícula** tiene ahora valores enteros y flotantes.

## <a name="examine-the-settings-file"></a>Examinar el archivo de configuración
 En esta sección, exportará los valores de categoría de propiedad a un archivo de configuración. Examine el archivo y, a continuación, importe los valores de nuevo en la categoría de la propiedad.

1. Inicie el proyecto en modo de depuración presionando **F5**. Esto inicia la instancia experimental.

2. Abra el **Tools**  >  cuadro de diálogo **Opciones** de herramientas.

3. En la vista de árbol del panel izquierdo, expanda **mi categoría** y, a continuación, haga clic en **mi página de cuadrícula**.

4. Cambie el valor de **OptionFloat** a 3,1416 y **OptionInteger** a 12. Haga clic en **OK**.

5. En el menú **Herramientas**, haga clic en **Importar y exportar configuraciones**.

     Aparece el Asistente para **importar y exportar configuraciones** .

6. Asegúrese de que la **opción exportar configuración de entorno seleccionada** está seleccionada y, a continuación, haga clic en **siguiente**.

     Aparece la página **elegir la configuración que se va a exportar** .

7. Haga clic en **mi configuración**.

     La **Descripción** cambia a **OptionInteger y OptionFloat**.

8. Asegúrese de que **mi configuración** sea la única categoría seleccionada y, a continuación, haga clic en **siguiente**.

     Aparece la página **nombre del archivo de configuración** .

9. Asigne al nuevo archivo de configuración el nombre *Configurations. vssettings* y guárdelo en un directorio adecuado. Haga clic en **Finalizar**

     La página **exportar completada** indica que la configuración se ha exportado correctamente.

10. En el menú **Archivo** , seleccione **Abrir** y haga clic en **Archivo**. Busque el *parámetro Settings. vssettings* y ábralo.

     Puede encontrar la categoría de propiedades que exportó en la sección siguiente del archivo (los GUID serán distintos).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Tenga en cuenta que el nombre completo de la categoría se forma mediante la adición de un carácter de subrayado al nombre de la categoría, seguido del nombre del objeto. OptionFloat y OptionInteger aparecen en la categoría, junto con sus valores exportados.

11. Cierre el archivo de configuración sin cambiarlo.

12. En el menú **herramientas** , haga clic en **Opciones**, expanda **mi categoría**, haga clic en **mi página de cuadrícula** y, a continuación, cambie el valor de **OptionFloat** a 1,0 y **OptionInteger** a 1. Haga clic en **OK**.

13. En el menú **herramientas** , haga clic en **importar y exportar configuraciones**, seleccione **importar la configuración de entorno seleccionada** y, a continuación, haga clic en **siguiente**.

     Aparece la página **Guardar configuración actual** .

14. Seleccione **no, solo importar la nueva configuración** y, a continuación, haga clic en **siguiente**.

     Aparece la página **Elija una colección de configuraciones para importar** .

15. Seleccione el archivo *Configurations. vssettings* en el nodo **mi configuración** de la vista de árbol. Si el archivo no aparece en la vista de árbol, haga clic en **examinar** y búsquelo. Haga clic en **Siguiente**.

     Aparece el cuadro de diálogo **elegir la configuración que se va a importar** .

16. Asegúrese de que **la opción mi configuración** está seleccionada y, a continuación, haga clic en **Finalizar**. Cuando aparezca la página **importación completada** , haga clic en **cerrar**.

17. En el menú **herramientas** , haga clic en **Opciones**, expanda **mi categoría**, haga clic en **mi página de cuadrícula** y compruebe que se han restaurado los valores de categoría de propiedad.

---
title: Crear una categoría de configuración | Microsoft Docs
description: Obtenga información sobre cómo crear una Visual Studio de configuración y usarla para guardar y restaurar valores desde un archivo de configuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687610"
---
# <a name="create-a-settings-category"></a>Creación de una categoría de configuración

En este tutorial, creará una categoría Visual Studio configuración y la usará para guardar valores en un archivo de configuración y restaurarlos. Una categoría de configuración es un grupo de propiedades relacionadas que aparecen como un "punto de configuración personalizado"; es decir, como una casilla del Asistente **para importar y exportar configuraciones.** (Puede encontrarlo en el **menú** Herramientas). La configuración se guarda o restaura como una categoría y la configuración individual no se muestra en el asistente. Para obtener más información, vea [Configuración del entorno](../ide/environment-settings.md).

Para crear una categoría de configuración, se deriva de la <xref:Microsoft.VisualStudio.Shell.DialogPage> clase .

Para iniciar este tutorial, primero debe completar la primera sección de [la página Crear una opción](../extensibility/creating-an-options-page.md). La cuadrícula de propiedades Options resultante le permite examinar y cambiar las propiedades de la categoría . Después de guardar la categoría de propiedad en un archivo de configuración, examine el archivo para ver cómo se almacenan los valores de propiedad.

## <a name="prerequisites"></a>Prerrequisitos
 A partir Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en Visual Studio configuración. También puede instalar el SDK de VS después. Para más información, consulte [Instalación del SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Creación de una categoría de configuración
 En esta sección, usará un punto de configuración personalizado para guardar y restaurar los valores de la categoría de configuración.

### <a name="to-create-a-settings-category"></a>Para crear una categoría de configuración

1. Complete la [página Crear una opción](../extensibility/creating-an-options-page.md).

2. Abra el *archivo VSPackage.resx* y agregue estos tres recursos de cadena:

    |Nombre|Value|
    |----------|-----------|
    |106|Mi categoría|
    |107|Mi configuración|
    |108|OptionInteger y OptionFloat|

     Esto crea recursos que nombren la categoría "Mi categoría", el objeto "Mi configuración" y la descripción de categoría "OptionInteger y OptionFloat".

    > [!NOTE]
    > De estas tres, solo el nombre de categoría no aparece en el Asistente **para importar y exportar configuraciones.**

3. En *MyToolsOptionsPackage.cs,* agregue una propiedad denominada a `float` la clase , como se muestra en el ejemplo `OptionFloat` `OptionPageGrid` siguiente.

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
    > La `OptionPageGrid` categoría denominada "Mi categoría" ahora consta de las dos propiedades y `OptionInteger` `OptionFloat` .

4. Agregue un valor a la clase y asízcále el valor de CategoryName "My Category", asíégrele el valor de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` ObjectName "My Settings" y establezca isToolsOptionPage en true. Establezca categoryResourceID, objectNameResourceID y DescriptionResourceID en los identificadores de recursos de cadena correspondientes creados anteriormente.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compile la solución y comience la depuración. En la instancia experimental, debería ver que **Mi página de cuadrícula** ahora tiene valores enteros y float.

## <a name="examine-the-settings-file"></a>Examen del archivo de configuración
 En esta sección, exportará los valores de categoría de propiedad a un archivo de configuración. Examine el archivo y, a continuación, vuelva a importar los valores en la categoría de propiedad.

1. Inicie el proyecto en modo de depuración presionando **F5**. Esto inicia la instancia experimental.

2. Abra el **cuadro de diálogo** Opciones  >  **de** herramientas.

3. En la vista de árbol del panel izquierdo, expanda **Mi categoría** y, a continuación, haga clic en Mi página **de cuadrícula**.

4. Cambie el valor de **OptionFloat** a 3.1416 y **OptionInteger** a 12. Haga clic en **Aceptar**.

5. En el menú **Herramientas**, haga clic en **Importar y exportar configuraciones**.

     Aparece **el Asistente para importar y exportar** configuraciones.

6. Asegúrese de que **la opción Exportar configuración de entorno seleccionada** está seleccionada y, a continuación, haga clic en **Siguiente.**

     Aparece **la página Elegir configuración para** exportar.

7. Haga clic **en My Settings (Mi configuración).**

     La **descripción** cambia a **OptionInteger y OptionFloat.**

8. Asegúrese de que **Mi configuración es** la única categoría seleccionada y, a continuación, haga clic en **Siguiente.**

     Aparece **la página Nombre del archivo** de configuración.

9. Asigne al nuevo archivo de configuración el nombre *MySettings.vssettings* y guárdelo en un directorio adecuado. Haga clic en **Finalizar**

   El `.vssettings` archivo es el archivo Visual Studio configuración. El esquema del archivo está abierto. Normalmente, el esquema sigue una estructura XML donde cada categoría es una etiqueta, que a su vez puede contener etiquetas de subcategoría. Estas etiquetas de subcategoría pueden contener etiquetas de valor de propiedad. Aunque la mayoría de los paquetes usan la estructura común, cualquier paquete de Visual Studio puede aportar XML arbitrario al archivo con el esquema que elija.

   La **página Exportar completado** informa de que la configuración se exportó correctamente.

10. En el menú **Archivo** , seleccione **Abrir** y haga clic en **Archivo**. Busque *MySettings.vssettings* y ábralo.

     Puede encontrar la categoría de propiedad que exportó en la sección siguiente del archivo (los GUID serán diferentes).

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

     Observe que el nombre de categoría completo se forma mediante la adición de un carácter de subrayado al nombre de categoría seguido del nombre del objeto. OptionFloat y OptionInteger aparecen en la categoría, junto con sus valores exportados.

11. Cierre el archivo de configuración sin cambiarlo.

12. En  el **menú** Herramientas, haga clic en Opciones , expanda Mi categoría , haga clic en Mi página de cuadrícula y, a continuación, cambie el valor de **OptionFloat** a 1.0 y  **OptionInteger** a 1.  Haga clic en **Aceptar**.

13. En el **menú Herramientas,** haga clic **en Importar y exportar configuración,** seleccione **Importar la configuración de entorno seleccionada** y, a continuación, haga clic **en Siguiente.**

     Aparece **la página Guardar configuración** actual.

14. Seleccione **No, solo tiene que importar la nueva configuración** y, a continuación, haga clic en **Siguiente.**

     Aparece **la página Elegir una colección de configuraciones para** importar.

15. Seleccione el *archivo MySettings.vssettings* en el **nodo Mi configuración** de la vista de árbol. Si el archivo no aparece en la vista de árbol, haga clic **en Examinar** y bájelo. Haga clic en **Next**.

     Aparece **el cuadro de diálogo Elegir** configuración para importar.

16. Asegúrese de que **My Settings (Mi** configuración) está seleccionado y, a continuación, haga clic **en Finish (Finalizar).** Cuando aparezca **la página Importar completado,** haga clic **en Cerrar.**

17. En el **menú Herramientas** , haga clic en **Opciones**, expanda **Mi categoría**, haga clic en Mi página **de** cuadrícula y compruebe que se han restaurado los valores de categoría de propiedad.

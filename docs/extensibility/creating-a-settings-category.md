---
title: Creación de una categoría de configuración ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739609"
---
# <a name="create-a-settings-category"></a>Crear una categoría de configuración

En este tutorial se crea una categoría de configuración de Visual Studio y se usa para guardar los valores y restaurar los valores de un archivo de configuración. Una categoría de configuración es un grupo de propiedades relacionadas que aparecen como un "punto de configuración personalizado"; es decir, como casilla de verificación en el asistente **Importar y exportación de configuración.** (Puede encontrarlo en el menú **Herramientas.)** La configuración se guarda o restaura como una categoría, y la configuración individual no se muestra en el asistente. Para obtener más información, vea [Configuración del entorno](../ide/environment-settings.md).

Puede crear una categoría de configuración <xref:Microsoft.VisualStudio.Shell.DialogPage> derivando de la clase.

Para iniciar este tutorial, primero debe completar la primera sección de [la página Crear una página de opciones](../extensibility/creating-an-options-page.md). La cuadrícula de propiedades Opciones resultante le permite examinar y cambiar las propiedades de la categoría. Después de guardar la categoría de propiedad en un archivo de configuración, examine el archivo para ver cómo se almacenan los valores de propiedad.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-settings-category"></a>Crear una categoría de configuración
 En esta sección, se utiliza un punto de configuración personalizado para guardar y restaurar los valores de la categoría de configuración.

### <a name="to-create-a-settings-category"></a>Para crear una categoría de configuración

1. Complete la [página Crear opciones](../extensibility/creating-an-options-page.md).

2. Abra el archivo *VSPackage.resx* y agregue estos tres recursos de cadena:

    |Nombre|Value|
    |----------|-----------|
    |106|Mi categoría|
    |107|Mi configuración|
    |108|OptionInteger y OptionFloat|

     Esto crea recursos que nombran la categoría "Mi categoría", el objeto "Mi configuración" y la descripción de categoría "OptionInteger y OptionFloat".

    > [!NOTE]
    > De estos tres, solo el nombre de la categoría no aparece en el asistente **Importar y exportar configuración.**

3. En *MyToolsOptionsPackage.cs*, `float` agregue `OptionFloat` una `OptionPageGrid` propiedad con nombre a la clase, como se muestra en el ejemplo siguiente.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > La `OptionPageGrid` categoría denominada "Mi categoría" ahora `OptionInteger` consta `OptionFloat`de las dos propiedades y .

4. Agregue <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> un `MyToolsOptionsPackage` a a la clase y asíbóeles el CategoryName "My Category", asírácele el ObjectName "My Settings" y establezca isToolsOptionPage en true. Establezca categoryResourceID, objectNameResourceID y DescriptionResourceID en los identificadores de recursos de cadena correspondientes creados anteriormente.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compile la solución y comience la depuración. En la instancia experimental debería ver que **Mi página** de cuadrícula ahora tiene valores enteros y flotantes.

## <a name="examine-the-settings-file"></a>Examine el archivo de configuración
 En esta sección, exportará los valores de categoría de propiedad a un archivo de configuración. Examine el archivo y, a continuación, vuelva a importar los valores en la categoría de propiedad.

1. Inicie el proyecto en modo de depuración presionando **F5**. Esto inicia la instancia experimental.

2. Abra el cuadro de diálogo**Opciones** **de herramientas.** > 

3. En la vista de árbol del panel izquierdo, expanda **Mi categoría** y, a continuación, haga clic en Mi página de **cuadrícula**.

4. Cambie el valor de **OptionFloat** a 3.1416 y **OptionInteger** a 12. Haga clic en **OK**.

5. En el menú **Herramientas**, haga clic en **Importar y exportar configuraciones**.

     Aparece el asistente **Importar y exportar parámetros.**

6. Asegúrese de que la opción Exportar configuración de **entorno seleccionada** esté seleccionada y, a continuación, haga clic en **Siguiente**.

     Aparece la página **Elegir configuración para exportar.**

7. Haga clic en **Mi configuración**.

     La **descripción** cambia a **OptionInteger y OptionFloat**.

8. Asegúrese de que **Mi configuración** es la única categoría seleccionada y, a continuación, haga clic en **Siguiente**.

     Aparece la página Nombre del archivo de **configuración.**

9. Asigne al nuevo archivo de configuración el nombre *MySettings.vssettings* y guárdelo en un directorio adecuado. Haga clic en **Finalizar**

     La página **Exportar completado** informa de que la configuración se ha exportado correctamente.

10. En el menú **Archivo** , seleccione **Abrir**y haga clic en **Archivo**. Busque *MySettings.vssettings* y ábralo.

     Puede encontrar la categoría de propiedad que exportó en la siguiente sección del archivo (sus GUID diferirán).

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

     Observe que el nombre completo de la categoría está formado por la adición de un carácter de subrayado al nombre de categoría seguido del nombre del objeto. OptionFloat y OptionInteger aparecen en la categoría, junto con sus valores exportados.

11. Cierre el archivo de configuración sin cambiarlo.

12. En el menú **Herramientas** , haga clic en **Opciones**, expanda **Mi categoría**, haga clic en Mi página de **cuadrícula** y, a continuación, cambie el valor de **OptionFloat** a 1.0 y **OptionInteger** a 1. Haga clic en **OK**.

13. En el menú **Herramientas** , haga clic en **Importar y exportar configuración**, seleccione Importar configuración de entorno **seleccionada**y, a continuación, haga clic en **Siguiente**.

     Aparece la página **Guardar configuración actual.**

14. Seleccione **No, solo tiene que importar la nueva configuración** y, a continuación, haga clic en **Siguiente**.

     Aparece la página **Elegir una colección de configuraciones para importar.**

15. Seleccione el archivo *MySettings.vssettings* en el nodo **Mis configuraciones** de la vista de árbol. Si el archivo no aparece en la vista de árbol, haga clic en **Examinar** y búsquelo. Haga clic en **Next**.

     Aparece el cuadro de diálogo **Elegir configuración para importar.**

16. Asegúrese de que **Mi configuración** está seleccionada y, a continuación, haga clic en **Finalizar**. Cuando aparezca la página **Importar completada,** haga clic en **Cerrar**.

17. En el menú **Herramientas** , haga clic en **Opciones**, expanda **Mi categoría**, haga clic en Mi página de **cuadrícula** y compruebe que se han restaurado los valores de categoría de propiedad.

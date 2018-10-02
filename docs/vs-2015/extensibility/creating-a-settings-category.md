---
title: Creación de una categoría de configuración | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91c46e5a222526dd68d98be0c855067cd96b10f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573755"
---
# <a name="creating-a-settings-category"></a>Creación de una categoría de configuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [crear una categoría de configuración](https://docs.microsoft.com/visualstudio/extensibility/creating-a-settings-category).  
  
En este tutorial crea una categoría de configuración de Visual Studio y usarlo para guardar los valores para y restaurar los valores de un archivo de configuración. Una categoría de configuración es un grupo de propiedades relacionadas que aparecen como un "punto de configuración personalizada;" es decir, como una casilla en la **importar y configuraciones de exportaciones** asistente. (Puede encontrarlo en el **herramientas** menú.) Configuración se guarda o se restaura como una categoría y opciones de configuración individuales no se muestran en el asistente. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Crear una categoría de configuración mediante la derivación desde el <xref:Microsoft.VisualStudio.Shell.DialogPage> clase.  
  
 Para iniciar este tutorial, primero debe completar la primera sección del [creación de una página de opciones](../extensibility/creating-an-options-page.md). La cuadrícula de propiedades opciones resultante le permite examinar y cambiar las propiedades de la categoría. Después de guardar la categoría de propiedad en un archivo de configuración, examine el archivo para ver cómo se almacenan los valores de propiedad.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Creación de una categoría de configuración  
 En esta sección, se usa un punto de configuración personalizada para guardar y restaurar los valores de la categoría de configuración.  
  
#### <a name="to-create-a-settings-category"></a>Para crear una categoría de configuración  
  
1.  Completar la [creación de una página de opciones](../extensibility/creating-an-options-page.md).  
  
2.  Abra el archivo VSPackage.resx y agregar estos recursos de tres cadena:  
  
    |nombre|Valor|  
    |----------|-----------|  
    |106|Mi categoría|  
    |107|Mi configuración|  
    |108|OptionInteger y OptionFloat|  
  
     Esto crea los recursos de ese nombre de la categoría "My Category", el objeto "My Settings" y la descripción de la categoría "OptionInteger y OptionFloat".  
  
    > [!NOTE]
    >  De estos tres, solo el nombre de categoría no aparecen en el Asistente para importar y exportar configuraciones.  
  
3.  En MyToolsOptionsPackage.cs, agregue un `float` propiedad denominada `OptionFloat` a la `OptionPageGrid` clase, como se muestra en el ejemplo siguiente.  
  
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
    >  El `OptionPageGrid` categoría denominada "My Category" ahora consta de las dos propiedades, `OptionInteger` y `OptionFloat`.  
  
4.  Agregar un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a la `MyToolsOptionsPackage` clase y asígnele el nombre de categoría "My Category", asígnele el ObjectName "My Settings" y isToolsOptionPage se establece en true. Establecer categoryResourceID, objectNameResourceID y DescriptionResourceID al recurso de cadena correspondiente que identificadores creados anteriormente.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Compile la solución y comience la depuración. En la instancia experimental debería ver que **mi página de cuadrícula** ahora tiene valores enteros y flotantes.  
  
## <a name="examining-the-settings-file"></a>Examine el archivo de configuración  
 En esta sección, exportará los valores de categoría de propiedad a un archivo de configuración. Examine el archivo y, a continuación, importe los valores en la categoría de propiedad.  
  
1.  Inicie el proyecto en modo de depuración presionando F5. Esto inicia la instancia experimental.  
  
2.  Abra el **herramientas / opciones** cuadro de diálogo.  
  
3.  En la vista de árbol en el panel izquierdo, expanda **My Category** y, a continuación, haga clic en **mi página de cuadrícula**.  
  
4.  Cambie el valor de **OptionFloat** a 3,1416 y **OptionInteger** en 12. Haga clic en **Aceptar**.  
  
5.  En el **herramientas** menú, haga clic en **importar y exportar configuraciones**.  
  
     El **importar y exportar configuraciones** aparece el asistente.  
  
6.  Asegúrese de que **exportar la configuración de entorno seleccionada** está seleccionada y, a continuación, haga clic en **siguiente**.  
  
     El **elija la configuración para exportar** aparece la página.  
  
7.  Haga clic en **mi configuración**.  
  
     El **descripción** cambia a **OptionInteger y OptionFloat**.  
  
8.  Asegúrese de que **mi configuración** es la única categoría que está seleccionada y, a continuación, haga clic en **siguiente**.  
  
     El **nombre su archivo de configuración** aparece la página.  
  
9. Asigne al nuevo archivo de configuración `MySettings.vssettings` y guárdelo en un directorio adecuado. Haga clic en **Finalizar**.  
  
     El **exportación completa** página informa de que la configuración se exportaron correctamente.  
  
10. En el **archivo** menú, elija **abierto**y, a continuación, haga clic en **archivo**. Busque `MySettings.vssettings` y ábralo.  
  
     Puede encontrar la categoría de propiedad que se exportó en la siguiente sección del archivo (el GUID será diferente).  
  
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
  
     Tenga en cuenta que el nombre de categoría completa se forma mediante la adición de un carácter de subrayado en el nombre de categoría seguido del nombre de objeto. OptionFloat y OptionInteger aparecen en la categoría, junto con sus valores exportados.  
  
11. Cierre el archivo de configuración sin cambiarlo.  
  
12. En el **herramientas** menú, haga clic en **opciones**, expanda **My Category**, haga clic en **mi página de cuadrícula** y, a continuación, cambie el valor de  **OptionFloat** a 1.0 y **OptionInteger** en 1. Haga clic en **Aceptar**.  
  
13. En el **herramientas** menú, haga clic en **importar y exportar configuraciones**, seleccione **importar la configuración de entorno seleccionada**y, a continuación, haga clic en **siguiente**.  
  
     El **Guardar configuración actual** aparece la página.  
  
14. Seleccione **No, solo importar la nueva configuración** y, a continuación, haga clic en **siguiente**.  
  
     El **elija una colección de configuraciones para importar** aparece la página.  
  
15. Seleccione el `MySettings.vssettings` de archivos en el **mi configuración** nodo de la vista de árbol. Si el archivo no aparece en la vista de árbol, haga clic en **examinar** y encontrarlo. Haga clic en **Siguiente**.  
  
     El **elija la configuración para importar** aparece el cuadro de diálogo.  
  
16. Asegúrese de que **mi configuración** está seleccionada y, a continuación, haga clic en **finalizar**. Cuando el **importación completada** aparece en la página, haga clic en **cerrar**.  
  
17. En el **herramientas** menú, haga clic en **opciones**, expanda **My Category**, haga clic en **mi página de cuadrícula** y compruebe que dispone de los valores de categoría de propiedad se ha restaurado.


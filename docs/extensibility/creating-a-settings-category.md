---
title: "Creaci&#243;n de una categor&#237;a de configuraci&#243;n | Microsoft Docs"
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
  - "configuración del perfil, crear categorías"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
caps.handback.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
---
# Creaci&#243;n de una categor&#237;a de configuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial crea una categoría de configuración de Visual Studio y usarlo para guardar los valores para y restaurar los valores de un archivo de configuración. Una categoría de configuración es un grupo de propiedades relacionadas que aparecen como "punto de configuración personalizada"; es decir, como una casilla de verificación en el **Importar y exporta configuraciones** asistente. \(Puede encontrar en el **herramientas** menú.\) Configuración se guarda o se restaura como una categoría y opciones de configuración individuales no aparecen en el asistente. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Crear una categoría de configuración mediante la derivación desde la <xref:Microsoft.VisualStudio.Shell.DialogPage> clase.  
  
 Para iniciar este tutorial, primero debe completar la primera sección del [Creación de una página de opciones](../extensibility/creating-an-options-page.md). La cuadrícula de propiedades opciones resultante le permite examinar y cambiar las propiedades de la categoría. Después de guardar la categoría de propiedad en un archivo de configuración, examine el archivo para ver cómo se almacenan los valores de propiedad.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creación de una categoría de configuración  
 En esta sección, se usa un punto de una configuración personalizada para guardar y restaurar los valores de la categoría de configuración.  
  
#### Para crear una categoría de configuración  
  
1.  Completar la [Creación de una página de opciones](../extensibility/creating-an-options-page.md).  
  
2.  Abra el archivo VSPackage.resx y agregar estas tres cadenas de recursos:  
  
    |Nombre|Valor|  
    |------------|-----------|  
    |106|Mi categoría|  
    |107|Mi configuración|  
    |108|OptionInteger y OptionFloat|  
  
     Esto crea los recursos de nombre de la categoría "My Category", el objeto "Mi configuración" y la descripción de la categoría "OptionInteger y OptionFloat".  
  
    > [!NOTE]
    >  De estos tres, el nombre de la categoría no aparece en el Asistente para importar y exportar configuraciones.  
  
3.  En MyToolsOptionsPackage.cs, agregue un `float` propiedad denominada `OptionFloat` para el `OptionPageGrid` de clase, como se muestra en el ejemplo siguiente.  
  
    ```c#  
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
    >  El `OptionPageGrid` categoría denominada "My Category" ahora consta de las dos propiedades, `OptionInteger` y `OptionFloat`.  
  
4.  Agregar una <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a la `MyToolsOptionsPackage` clase y asígnele el nombre "My Category" CategoryName, asígnele ObjectName "Mi configuración" y isToolsOptionPage se establece en true. Establezca los categoryResourceID, objectNameResourceID y DescriptionResourceID en el recurso de cadena correspondiente que identificadores creados anteriormente.  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Compile la solución y comience la depuración. En la instancia experimental verá que **Mi página de cuadrícula** ahora tiene valores enteros y flotantes.  
  
## Examinar el archivo de configuración.  
 En esta sección, exportar valores de categoría de propiedad a un archivo de configuración. Examine el archivo y, a continuación, importar los valores de la categoría de propiedad.  
  
1.  Iniciar el proyecto en modo de depuración presionando F5. Esto inicia la instancia experimental.  
  
2.  Abra la **Herramientas \/ opciones** cuadro de diálogo.  
  
3.  En la vista de árbol en el panel izquierdo, expanda **My Category** y, a continuación, haga clic en **Mi página de cuadrícula**.  
  
4.  Cambie el valor de **OptionFloat** a 3.1416 y **OptionInteger** a 12. Haga clic en **Aceptar**.  
  
5.  En el menú **Herramientas**, haga clic en **Importar y exportar configuraciones**.  
  
     El **Importar y exportar configuraciones** aparece el asistente.  
  
6.  Asegúrese de que **exportar la configuración de entorno seleccionada** está seleccionada y, a continuación, haga clic en **siguiente**.  
  
     El **Elegir la configuración de la exportación** aparece la página.  
  
7.  Haga clic en **Mi configuración**.  
  
     El **descripción** cambia a **OptionInteger y OptionFloat**.  
  
8.  Asegúrese de que **Mi configuración** es la única categoría que está seleccionada y, a continuación, haga clic en **siguiente**.  
  
     El **nombre su archivo de configuración** aparece la página.  
  
9. Asigne al nuevo archivo de configuración `MySettings.vssettings` y guárdela en un directorio adecuado. Haga clic en **Finalizar**.  
  
     El **exportación completa** página informa de que la configuración se ha exportado correctamente.  
  
10. En el **archivo** menú, seleccione **abiertos**, y, a continuación, haga clic en **archivo**. Busque `MySettings.vssettings` y ábralo.  
  
     Puede encontrar la categoría de propiedad que se exportó en la siguiente sección del archivo \(el GUID será distinto\).  
  
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
  
     Observe que el nombre de categoría completa está formado por la adición de un carácter de subrayado en el nombre de categoría seguido del nombre de objeto. OptionFloat y OptionInteger aparecen en la categoría, junto con sus valores exportados.  
  
11. Cierre el archivo de configuración sin modificarlo.  
  
12. En el **herramientas** menú, haga clic en **opciones**, expanda **My Category**, haga clic en **Mi página de cuadrícula** y, a continuación, cambie el valor de **OptionFloat** a 1.0 y **OptionInteger** en 1. Haga clic en **Aceptar**.  
  
13. En el **herramientas** menú, haga clic en **Importar y exportar configuraciones**, seleccione **importar la configuración de entorno seleccionada**, y, a continuación, haga clic en **siguiente**.  
  
     El **Guardar configuración actual** aparece la página.  
  
14. Seleccione **No, sólo importar la nueva configuración** y, a continuación, haga clic en **siguiente**.  
  
     El **Elija una colección de configuraciones para importar** aparece la página.  
  
15. Seleccione el `MySettings.vssettings` de archivo en el **Mi configuración** nodo de la vista de árbol. Si el archivo no aparece en la vista de árbol, haga clic en **Examinar** y encontrarlo. Haga clic en **Siguiente**.  
  
     El **Elegir configuraciones para importar** aparece el cuadro de diálogo.  
  
16. Asegúrese de que **Mi configuración** está seleccionada y, a continuación, haga clic en **Finalizar**. Cuando el **Importación completada** aparece en la página, haga clic en **Cerrar**.  
  
17. En el **herramientas** menú, haga clic en **opciones**, expanda **My Category**, haga clic en **Mi página de cuadrícula** y compruebe que se restauraron los valores de categoría de propiedad.
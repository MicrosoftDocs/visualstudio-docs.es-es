---
title: "Actualizar las áreas de formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5 | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 5c2f3e3951ac46a2459545b51fafa45ecc6b86f9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="updating-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Actualizar las áreas del formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5
  Si el marco de trabajo de destino de un proyecto de complemento de VSTO de Outlook con un área de formulario se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe realizar algunos cambios en el código de área del formulario generado y en cualquier código que cree instancias de determinadas clases de área del formulario en tiempo de ejecución.  
  
## <a name="updating-the-generated-form-region-code"></a>Actualizar el código de área del formulario generado  
 Si se cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe cambiar el código de área del formulario generado. Los cambios que se realizan son diferentes para las áreas del formulario diseñadas en Visual Studio y para las áreas del formulario importadas de Outlook. Para más información sobre las diferencias entre estos tipos de áreas del formulario, consulte [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Para actualizar el código generado para un área del formulario diseñada en Visual Studio  
  
1.  Abra el archivo de código subyacente del área del formulario en el editor de código. Este archivo se llama *YourFormRegion*.Designer.cs o *YourFormRegion*.Designer.vb. Para ver este archivo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones**.  
  
2.  Modifique la declaración de la clase de área de formulario para que se derive de <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> en lugar de Microsoft.Office.Tools.Outlook.FormRegionControl.  
  
3.  Modifique el constructor de la clase de área del formulario tal como se muestra en los ejemplos de código siguientes.  
  
     En el ejemplo de código siguiente se muestra el constructor de una clase de área del formulario de un proyecto destinado a .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     En el ejemplo de código siguiente se muestra el constructor de una clase de área del formulario de un proyecto destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  Modifique la firma del método `InitializeManifest` tal como se muestra a continuación. Asegúrese de que no modifica el código del método; este código representa la configuración del área del formulario que aplicó en el diseñador. En proyectos de Visual C#, debe expandir el área llamada `Form Region Designer generated code` para ver este método.  
  
     En el ejemplo de código siguiente se muestra la firma del método `InitializeManifest` de un proyecto destinado a .NET Framework 3.5.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     En el ejemplo de código siguiente se muestra la firma del método `InitializeManifest` de un proyecto destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  Agregue un nuevo elemento de área del formulario de Outlook a su proyecto. Abra el archivo de código subyacente de la nueva área del formulario, busque las clases *YourNewFormRegion*`Factory` y `WindowFormRegionCollection` en el archivo y copie estas clases en el Portapapeles.  
  
6.  Elimine la nueva área del formulario que agregó al proyecto.  
  
7.  En el archivo de código subyacente del área del formulario que está actualizando para que funcione en el proyecto redestinado, busque las clases *YourOriginalFormRegion*`Factory` y `WindowFormRegionCollection` y reemplácelas con el código que copió de la nueva área del formulario.  
  
8.  En las clases *YourNewFormRegion*`Factory` y `WindowFormRegionCollection` , busque todas las referencias a la clase *YourNewFormRegion* y cámbielas a la clase *YourOriginalFormRegion* . Por ejemplo, si el área del formulario que está actualizando se llama `SalesDataFormRegion` y la nueva área del formulario que creó en el paso 5 se llama `FormRegion1`, cambie todas las referencias de `FormRegion1` a `SalesDataFormRegion`.  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Para actualizar el código generado para un área del formulario importada de Outlook  
  
1.  Abra el archivo de código subyacente del área del formulario en el editor de código. Este archivo se llama *YourFormRegion*.Designer.cs o *YourFormRegion*.Designer.vb. Para ver este archivo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones**.  
  
2.  Modifique la declaración de la clase de área de formulario para que se derive de <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> en lugar de Microsoft.Office.Tools.Outlook.ImportedFormRegion.  
  
3.  Modifique el constructor de la clase de área del formulario tal como se muestra en los ejemplos de código siguientes.  
  
     En el ejemplo de código siguiente se muestra el constructor de una clase de área del formulario de un proyecto destinado a .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     En el ejemplo de código siguiente se muestra la firma del constructor de una clase de área del formulario de un proyecto destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  Para cada línea de código del método `InitializeControls` que inicialice un control en la clase de área del formulario, modifique el código tal como se muestra a continuación.  
  
     En el ejemplo de código siguiente se muestra la manera de inicializar un control en un proyecto destinado a .NET Framework 3.5. En este código, el método GetFormRegionControl tiene un parámetro de tipo que especifica el tipo del control que se devuelve.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     En el ejemplo de código siguiente se muestra la manera de inicializar un control en un proyecto destinado a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. En este código, el método <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> no tiene un parámetro de tipo. Debe convertir el valor devuelto al tipo del control que se está inicializando.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Agregue un nuevo elemento de área del formulario de Outlook a su proyecto. Abra el archivo de código subyacente de la nueva área del formulario, busque las clases *YourNewFormRegion*`Factory` y `WindowFormRegionCollection` en el archivo y copie estas clases en el Portapapeles.  
  
6.  Elimine la nueva área del formulario que agregó al proyecto.  
  
7.  En el archivo de código subyacente del área del formulario que está actualizando para que funcione en el proyecto redestinado, busque las clases *YourOriginalFormRegion*`Factory` y `WindowFormRegionCollection` y reemplácelas con el código que copió de la nueva área del formulario.  
  
8.  En las clases *YourNewFormRegion*`Factory` y `WindowFormRegionCollection` , busque todas las referencias a la clase *YourNewFormRegion* y cámbielas a la clase *YourOriginalFormRegion* . Por ejemplo, si el área del formulario que está actualizando se llama `SalesDataFormRegion` y la nueva área del formulario que creó en el paso 5 se llama `FormRegion1`, cambie todas las referencias de `FormRegion1` a `SalesDataFormRegion`.  
  
## <a name="instantiating-form-region-classes"></a>Crear instancias de clases de área del formulario  
 Debe modificar todo el código que cree dinámicamente instancias de determinadas clases de área del formulario. En los proyectos que tienen como destino .NET Framework 3.5, puede crear instancias de clases de área de formulario como Microsoft.Office.Tools.Outlook.FormRegionManifest directamente. En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estas clases son interfaces de las que no se puede crear instancias directamente.  
  
 Si se cambia la plataforma de destino del proyecto a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe crear instancias de las interfaces mediante los métodos proporcionados por la propiedad Globals.Factory. Para obtener más información acerca de la propiedad Globals.Factory, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 En la tabla siguiente se enumeran los tipos de áreas del formulario y el método que se usa para crear instancias de los tipos en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.  
  
|Tipo|Método de generador que se usa|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>Vea también  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Creación de áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)  
  
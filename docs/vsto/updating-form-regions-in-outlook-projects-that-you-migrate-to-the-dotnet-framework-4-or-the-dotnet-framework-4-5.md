---
title: Actualizar las áreas de formulario de Outlook en los proyectos migrados a .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7e300cd9f6f7d631a029310b01fbfdad7cb4686
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836044"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Actualice las áreas de formulario en los proyectos de Outlook que migre al .NET Framework 4 o al .NET Framework 4,5
  Si el marco de trabajo de destino de un proyecto de complemento de VSTO de Outlook con un área de formulario se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe realizar algunos cambios en el código de área del formulario generado y en cualquier código que cree instancias de determinadas clases de área del formulario en tiempo de ejecución.

## <a name="update-the-generated-form-region-code"></a>Actualizar el código de área del formulario generado
 Si se cambia el marco de trabajo de destino del proyecto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe cambiar el código de área del formulario generado. Los cambios que se realizan son diferentes para las áreas del formulario diseñadas en Visual Studio y para las áreas del formulario importadas de Outlook. Para obtener más información sobre las diferencias entre estos tipos de áreas de formulario, consulte [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Para actualizar el código generado para un área del formulario diseñada en Visual Studio

1. Abra el archivo de código subyacente del área del formulario en el editor de código. Este archivo se llama *YourFormRegion*.Designer.cs o *YourFormRegion*.Designer.vb. Para ver este archivo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones**.

2. Modifique la declaración de la clase de área del formulario para que se derive de <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> en lugar de `Microsoft.Office.Tools.Outlook.FormRegionControl`.

3. Modifique el constructor de la clase de área del formulario tal como se muestra en los ejemplos de código siguientes.

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

4. Modifique la firma del método `InitializeManifest` tal como se muestra a continuación. Asegúrese de que no modifica el código del método; este código representa la configuración del área del formulario que aplicó en el diseñador. En proyectos de Visual C#, debe expandir el área llamada `Form Region Designer generated code` para ver este método.

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

5. Agregue un nuevo elemento de área del formulario de Outlook a su proyecto. Abra el archivo de código subyacente de la nueva área de formulario, busque las clases *clases yournewformregion* `Factory` y `WindowFormRegionCollection` en el archivo y copie estas clases en el portapapeles.

6. Elimine la nueva área del formulario que agregó al proyecto.

7. En el archivo de código subyacente del área de formulario que está actualizando para trabajar en el proyecto redestinado, busque las clases *YourOriginalFormRegion* `Factory` y `WindowFormRegionCollection` y reemplácelas con el código que copió de la nueva área de formulario.

8. En las clases *clases yournewformregion* `Factory` y `WindowFormRegionCollection` , busque todas las referencias a la clase *clases yournewformregion* y cambie cada referencia a la clase *YourOriginalFormRegion* en su lugar. Por ejemplo, si el área del formulario que está actualizando se llama `SalesDataFormRegion` y la nueva área del formulario que creó en el paso 5 se llama `FormRegion1`, cambie todas las referencias de `FormRegion1` a `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Para actualizar el código generado para un área del formulario importada de Outlook

1. Abra el archivo de código subyacente del área del formulario en el editor de código. Este archivo se llama *YourFormRegion*.Designer.cs o *YourFormRegion*.Designer.vb. Para ver este archivo en los proyectos de Visual Basic, haga clic en el botón **Mostrar todos los archivos** del **Explorador de soluciones**.

2. Modifique la declaración de la clase de área del formulario para que se derive de <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> en lugar de `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.

3. Modifique el constructor de la clase de área del formulario tal como se muestra en los ejemplos de código siguientes.

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

4. Para cada línea de código del método `InitializeControls` que inicialice un control en la clase de área del formulario, modifique el código tal como se muestra a continuación.

     En el ejemplo de código siguiente se muestra la manera de inicializar un control en un proyecto destinado a .NET Framework 3.5. En este código, el método `GetFormRegionControl` tiene un parámetro de tipo que especifica el tipo del control que se devuelve.

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

5. Agregue un nuevo elemento de área del formulario de Outlook a su proyecto. Abra el archivo de código subyacente de la nueva área de formulario, busque las clases *clases yournewformregion* `Factory` y `WindowFormRegionCollection` en el archivo y copie estas clases en el portapapeles.

6. Elimine la nueva área del formulario que agregó al proyecto.

7. En el archivo de código subyacente del área de formulario que está actualizando para trabajar en el proyecto redestinado, busque las clases *YourOriginalFormRegion* `Factory` y `WindowFormRegionCollection` y reemplácelas con el código que copió de la nueva área de formulario.

8. En las clases *clases yournewformregion* `Factory` y `WindowFormRegionCollection` , busque todas las referencias a la clase *clases yournewformregion* y cambie cada referencia a la clase *YourOriginalFormRegion* en su lugar. Por ejemplo, si el área del formulario que está actualizando se llama `SalesDataFormRegion` y la nueva área del formulario que creó en el paso 5 se llama `FormRegion1`, cambie todas las referencias de `FormRegion1` a `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Crear instancias de clases de área de formulario
 Debe modificar todo el código que cree dinámicamente instancias de determinadas clases de área del formulario. En proyectos destinados a .NET Framework 3.5, puede crear instancias de clases de área del formulario como `Microsoft.Office.Tools.Outlook.FormRegionManifest` directamente. En los proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, estas clases son interfaces de las que no se puede crear instancias directamente.

 Si la plataforma de destino del proyecto se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe crear instancias de las interfaces mediante los métodos proporcionados por la propiedad `Globals.Factory`. Para obtener más información sobre la `Globals.Factory` propiedad, consulte [acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

 En la tabla siguiente se enumeran los tipos de áreas del formulario y el método que se usa para crear instancias de los tipos en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores.

|Tipo|Método de generador que se usa|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Consulte también
- [Migrar soluciones de Office al .NET Framework 4 o posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)

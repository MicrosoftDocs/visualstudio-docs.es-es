---
title: 'Tutorial: Llamar a código desde VBA en un proyecto de Visual C#'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2803ef31ec1009215d4490ac527c42cbdc90571
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781694"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Tutorial: Llamar a código desde VBA en un proyecto de Visual C#
  Este tutorial muestra cómo llamar a un método en una personalización de nivel de documento para Microsoft Office Excel desde el código de Visual Basic para Aplicaciones (VBA) del libro. El procedimiento implica tres pasos básicos: agregar un método a la clase de elemento host `Sheet1` , exponer el método a código VBA del libro y llamar al método desde código VBA del libro.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aunque en este tutorial se usa Excel específicamente, los conceptos que se muestran en el tutorial también se aplican a los proyectos de nivel de documento para Word.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un libro que contenga código VBA.  
  
-   Confiar en la ubicación del libro usando el Centro de confianza de Excel.  
  
-   Agregar un método a la clase de elemento host `Sheet1` .  
  
-   Extraer una interfaz para la clase de elemento host `Sheet1` .  
  
-   Exponer el método a código VBA.  
  
-   Llamar al método desde código VBA.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-a-workbook-that-contains-vba-code"></a>Crear un libro que contenga código VBA  
 El primer paso consiste en crear un libro habilitado para macros que contenga una macro VBA sencilla. Antes de exponer el código de una personalización a VBA, el libro ya debe contener código VBA. De lo contrario, Visual Studio no puede modificar el proyecto de VBA para que el código VBA pueda llamar al ensamblado de personalización.  
  
 Si ya tiene un libro que contiene código VBA y desea usarlo, puede omitir este paso.  
  
### <a name="to-create-a-workbook-that-contains-vba-code"></a>Para crear un libro que contenga código VBA  
  
1.  Inicie Excel.  
  
2.  Guardar el documento activo como un **libro de Excel habilitado para macros (\*.xlsm)** con el nombre **WorkbookWithVBA**. Guárdelo en una ubicación conveniente, como el escritorio.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el grupo **Código** , haga clic en **Visual Basic**.  
  
     Se abrirá el Editor de Visual Basic.  
  
5.  En la ventana **Proyecto** , haga doble clic en **ThisWorkbook**.  
  
     Se abrirá el archivo de código para el objeto `ThisWorkbook` .  
  
6.  Agregue el código VBA siguiente al archivo de código. Este código define una función simple que no hace nada. El único propósito de esta función es asegurarse de que existe un proyecto de VBA en el libro. Esto es necesario para los pasos posteriores de este tutorial.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Guarde el documento y salga de Excel.  
  
## <a name="create-the-project"></a>Crear el proyecto  
 Ahora puede crear un proyecto de nivel de documento para Excel que use el libro habilitado para macros creado anteriormente.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C#** y luego expanda **Office/SharePoint**.  
  
4.  Seleccione el nodo **Complementos de Office** .  
  
5.  En la lista de plantillas de proyecto, seleccione el proyecto **Libro de Excel 2010** o **Libro de Excel 2013** .  
  
6.  En el cuadro **Nombre** , escriba **CallingCodeFromVBA**.  
  
7.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .  
  
8.  Seleccione **Copiar un documento existente**y, en el cuadro **Ruta de acceso completa del documento existente** , especifique la ubicación del libro **WorkbookWithVBA** que creó anteriormente. Si usa su propio libro habilitado para macros, especifique la ubicación de dicho libro.  
  
9. Haga clic en **Finalizar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el libro **WorkbookWithVBA** en el diseñador y agrega el proyecto **CallingCodeFromVBA** al **Explorador de soluciones**.  
  
## <a name="trust-the-location-of-the-workbook"></a>Confíe en la ubicación del libro  
 Antes de exponer el código de la solución al código VBA del libro, debe confiar en el VBA del libro que se va a ejecutar. Existen varias formas de hacerlo. En este tutorial, llevará a cabo esta tarea confiando en la ubicación del libro en el **Centro de confianza** de Excel.  
  
### <a name="to-trust-the-location-of-the-workbook"></a>Para confiar en la ubicación del libro  
  
1.  Inicie Excel.  
  
2.  Haga clic en la pestaña **Archivo** .  
  
3.  Haga clic en el botón **Opciones de Excel** .  
  
4.  En el panel de categorías, haga clic en **Centro de confianza**.  
  
5.  En el panel de detalles, haga clic en **Configuración del Centro de confianza**.  
  
6.  En el panel de categorías, haga clic en **Ubicaciones de confianza**.  
  
7.  En el panel de detalles, haga clic en **Agregar nueva ubicación**.  
  
8.  En el cuadro de diálogo **Ubicación de confianza de Microsoft Office** , busque la carpeta que contiene el proyecto **CallingCodeFromVBA** .  
  
9. Seleccione **Las subcarpetas de esta ubicación también son de confianza**.  
  
10. En el cuadro de diálogo **Ubicación de confianza de Microsoft Office** , haga clic en **Aceptar**.  
  
11. En el cuadro de diálogo **Centro de confianza** , haga clic en **Aceptar**.  
  
12. En el cuadro de diálogo **Opciones de Excel** , haga clic en **Aceptar**.  
  
13. Salga de **Excel**.  
  
## <a name="add-a-method-to-the-sheet1-class"></a>Agregue un método a la clase Sheet1  
 Ahora que el proyecto de VBA está configurado, agregue un método público a la clase de elemento host `Sheet1` al que se pueda llamar desde código de VBA.  
  
### <a name="to-add-a-method-to-the-sheet1-class"></a>Para agregar un método a la clase Sheet1  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **Sheet1.cs**y, a continuación, haga clic en **Ver código**.  
  
     Se abre el archivo **Sheet1.cs** en el editor de código.  
  
2.  Agregue el código siguiente a la clase `Sheet1` . El método `CreateVstoNamedRange` crea un nuevo objeto <xref:Microsoft.Office.Tools.Excel.NamedRange> en el intervalo especificado. Este método también crea un controlador de eventos para el evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> de <xref:Microsoft.Office.Tools.Excel.NamedRange>. Más adelante en este tutorial, llamará al método `CreateVstoNamedRange` desde el código de VBA del documento.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Agregue el método siguiente a la clase `Sheet1`. Este método invalida el método <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> para devolver la instancia actual de la clase `Sheet1` .  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Aplique los atributos siguientes antes de la primera línea de la declaración de clase `Sheet1` . Estos atributos hacen que la clase sea visible para COM, pero sin generar una interfaz de clase.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extract-an-interface-for-the-sheet1-class"></a>Extraer una interfaz para la clase Sheet1  
 Antes de exponer el método `CreateVstoNamedRange` a código de VBA, debe crear una interfaz pública que defina este método y debe exponer esta interfaz a COM.  
  
### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Para extraer una interfaz para la clase Sheet1  
  
1.  En el archivo de código **Sheet1.cs** , haga clic en cualquier parte de la clase `Sheet1` .  
  
2.  En el menú **Refactorizar** , haga clic en **Extraer interfaz**.  
  
3.  En el cuadro de diálogo **Extraer interfaz** , en el cuadro **Seleccionar miembros públicos para formar la interfaz** , haga clic en la entrada para el método `CreateVstoNamedRange` .  
  
4.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] genera una nueva interfaz llamada `ISheet1`y modifica la definición de la clase `Sheet1` para que implemente la interfaz `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también abre el archivo **ISheet1.cs** en el Editor de código.  
  
5.  En el archivo **ISheet1.cs** , reemplace la declaración de interfaz `ISheet1` con el código siguiente. Este código hace pública la interfaz `ISheet1` y aplica el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> para hacer la interfaz visible para COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Compile el proyecto.  
  
## <a name="expose-the-method-to-vba-code"></a>Exponer el método a código VBA  
 Para exponer el método `CreateVstoNamedRange` a código VBA en el libro, establezca la propiedad **ReferenceAssemblyFromVbaProject** del elemento host `Sheet1` en **True**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>Para exponer el método a código VBA  
  
1.  En el **Explorador de soluciones**, haga doble clic en **Sheet1.cs**.  
  
     El archivo **WorkbookWithVBA** se abre en el diseñador, con Sheet1 visible.  
  
2.  En la ventana **Propiedades** , seleccione la propiedad **ReferenceAssemblyFromVbaProject** y cambie el valor a **True**.  
  
3.  Haga clic en **Aceptar** en el mensaje que se muestra.  
  
4.  Compile el proyecto.  
  
## <a name="call-the-method-from-vba-code"></a>Llame al método desde código VBA  
 Ahora puede llamar al método `CreateVstoNamedRange` desde el código VBA del libro.  
  
> [!NOTE]  
>  En este tutorial, agregará código VBA al libro mientras se depura el proyecto. El código VBA que agregue a este documento se sobrescribirá la siguiente vez que compile el proyecto, ya que Visual Studio reemplaza el documento de la carpeta de resultados de compilación por una copia del documento de la carpeta de proyecto principal. Si desea guardar el código VBA, puede copiarlo en el documento de la carpeta del proyecto. Para obtener más información, consulte [combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>Para llamar al método desde código VBA  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  En la pestaña **Desarrollador** , en el grupo **Código** , haga clic en **Visual Basic**.  
  
     Se abrirá el Editor de Visual Basic.  
  
3.  En el menú **Insertar** , haga clic en **Módulo**.  
  
4.  Agregue el siguiente código al nuevo módulo.  
  
     Este código llama al método `CreateTable` en el ensamblado de personalización. La macro accede a este método mediante el método global `GetManagedClass` para acceder a la clase de elemento host `Sheet1` que expuso al código VBA. El método `GetManagedClass` se generó automáticamente al establecer la propiedad **ReferenceAssemblyFromVbaProject** anteriormente en este tutorial.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Presione **F5**.  
  
6.  En el libro abierto, haga clic en la celda **A1** en **Sheet1**. Compruebe que aparece el cuadro de mensaje.  
  
7.  Salga de Excel sin guardar los cambios.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede obtener más información sobre cómo llamar a código en soluciones de Office desde VBA en estos temas:  
  
-   Llamar a código en un elemento host en una personalización de Visual Basic desde VBA. Este proceso es diferente del proceso de Visual C#. Para obtener más información, consulte [Tutorial: llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Llamar a código en un complemento de VSTO desde VBA. Para obtener más información, consulte [Tutorial: llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Vea también  
 [Combinar VBA y personalizaciones de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Cómo: exponer código a VBA en un proyecto de Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Cómo: exponer código a VBA en un Visual C&#35; proyecto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Tutorial: Llamar a código desde VBA en un proyecto de Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  
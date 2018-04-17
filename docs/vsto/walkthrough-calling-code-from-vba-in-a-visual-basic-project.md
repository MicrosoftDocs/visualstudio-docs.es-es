---
title: 'Tutorial: Llamar a código desde VBA en un proyecto de Visual Basic | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efb8f6c2759760fe2eb5c5d5ccf23e0942eac93a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-basic-project"></a>Tutorial: Llamar a código de VBA en un proyecto de Visual Basic
  Este tutorial muestra cómo llamar a un método en una personalización de nivel de documento para Microsoft Office Word desde el código de Visual Basic para Aplicaciones (VBA) del documento. El procedimiento implica tres pasos básicos: agregar un método a la clase de elemento host `ThisDocument` , exponer el método a código VBA y llamar al método desde código VBA del documento.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aunque en este tutorial se usa Word específicamente, los conceptos que se muestran en el tutorial también se aplican a los proyectos de nivel de documento para Excel.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un documento que contenga código VBA.  
  
-   Confiar en la ubicación del documento usando el Centro de confianza de Word.  
  
-   Agregar un método a la clase de elemento host `ThisDocument` .  
  
-   Exponer el método a código VBA.  
  
-   Llamar al método desde código VBA.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-a-document-that-contains-vba-code"></a>Crear un documento que contenga código VBA  
 El primer paso consiste en crear un documento habilitado para macros que contenga una macro VBA sencilla. El documento debe contener un proyecto de VBA antes de que se cree un proyecto de Visual Studio basado en el documento. De lo contrario, Visual Studio no puede modificar el proyecto de VBA para que el código VBA pueda llamar al ensamblado de personalización.  
  
 Si ya tiene un documento que contiene código VBA y desea usarlo, puede omitir este paso.  
  
#### <a name="to-create-a-document-that-contains-vba-code"></a>Para crear un documento que contenga código VBA  
  
1.  Inicie Word.  
  
2.  Guarde el documento activo como una palabra **documento habilitado para macros (\*.docm)** con el nombre **DocumentWithVBA**. Guárdelo en una ubicación conveniente, como el escritorio.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el grupo **Código** , haga clic en **Visual Basic**.  
  
     Se abrirá el Editor de Visual Basic.  
  
5.  En la ventana **Proyecto** , haga doble clic en **ThisDocument**.  
  
     Se abrirá el archivo de código para el objeto `ThisDocument` .  
  
6.  Agregue el código VBA siguiente al archivo de código. Este código define una función simple que no hace nada. El único propósito de esta función es asegurarse de que existe un proyecto de VBA en el documento. Esto es necesario para los pasos posteriores de este tutorial.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Guarde el documento y salga de Word.  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 Ahora puede crear un proyecto de nivel de documento para Word que use el documento habilitado para macros creado anteriormente.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**. Si su IDE está configurado para usar la configuración de desarrollo de Visual Basic, en el menú **Archivo** haga clic en **Nuevo proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual Basic**y luego expanda **Office/SharePoint**.  
  
4.  Seleccione el nodo **Complementos de Office** .  
  
5.  En la lista de plantillas de proyecto, seleccione el proyecto **Documento de Word 2010** o **Documento de Word 2013** .  
  
6.  En el cuadro **Nombre** , escriba **CallingCodeFromVBA**.  
  
7.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .  
  
8.  Seleccione **Copiar un documento existente**y, en el cuadro **Ruta de acceso completa del documento existente** , especifique la ubicación del documento **DocumentWithVBA** que creó anteriormente. Si usa su propio documento habilitado para macros, especifique la ubicación de dicho documento.  
  
9. Haga clic en **Finalizar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el documento **DocumentWithVBA** en el diseñador y agrega el proyecto **CallingCodeFromVBA** al **Explorador de soluciones**.  
  
## <a name="trusting-the-location-of-the-document"></a>Confiar en la ubicación del documento  
 Antes de exponer el código de la solución al código VBA del documento, debe confiar en el VBA del documento que se va a ejecutar. Existen varias formas de hacerlo. En este tutorial, confíe en la ubicación del documento en el **Centro de confianza** de Word.  
  
#### <a name="to-trust-the-location-of-the-document"></a>Para confiar en la ubicación del documento  
  
1.  Inicie Word.  
  
2.  Haga clic en la pestaña **Archivo** .  
  
3.  Haga clic en el botón **Opciones de Word** .  
  
4.  En el panel de categorías, haga clic en **Centro de confianza**.  
  
5.  En el panel de detalles, haga clic en **Configuración del Centro de confianza**.  
  
6.  En el panel de categorías, haga clic en **Ubicaciones de confianza**.  
  
7.  En el panel de detalles, haga clic en **Agregar nueva ubicación**.  
  
8.  En el cuadro de diálogo **Ubicación de confianza de Microsoft Office** , busque la carpeta que contiene el proyecto **CallingCodeFromVBA** .  
  
9. Seleccione **Las subcarpetas de esta ubicación también son de confianza**.  
  
10. En el cuadro de diálogo **Ubicación de confianza de Microsoft Office** , haga clic en **Aceptar**.  
  
11. En el cuadro de diálogo **Centro de confianza** , haga clic en **Aceptar**.  
  
12. En el cuadro de diálogo **Opciones de Word** , haga clic en **Aceptar**.  
  
13. Salga de Word.  
  
## <a name="adding-a-method-to-the-thisdocument-class"></a>Agregar un método a la clase ThisDocument  
 Ahora que el proyecto de VBA está configurado, agregue un método a la clase de elemento host `ThisDocument` al que se pueda llamar desde código de VBA.  
  
#### <a name="to-add-a-method-to-the-thisdocument-class"></a>Para agregar un método a la clase ThisDocument  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument.vb**y, a continuación, haga clic en **Ver código**.  
  
     Se abre el archivo **ThisDocument.vb** en el Editor de código.  
  
2.  Agregue el método siguiente a la clase `ThisDocument` . Este método crea una tabla con dos filas y dos columnas al principio del documento. Los parámetros especifican el texto que se muestra en la primera fila. Más adelante en este tutorial, llamará a este método desde el código de VBA del documento.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Compile el proyecto.  
  
## <a name="exposing-the-method-to-vba-code"></a>Exponer el método a código VBA  
 Para exponer el método `CreateTable` a código VBA del documento, establezca la propiedad **EnableVbaCallers** para el elemento host `ThisDocument` en **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Para exponer el método a código VBA  
  
1.  En el **Explorador de soluciones**, haga doble clic en **ThisDocument.vb**.  
  
     El archivo **DocumentWithVBA** se abre en el diseñador.  
  
2.  En la ventana **Propiedades** , seleccione la propiedad **EnableVbaCallers** y cambie el valor a **True**.  
  
3.  Haga clic en **Aceptar** en el mensaje que se muestra.  
  
4.  Compile el proyecto.  
  
## <a name="calling-the-method-from-vba-code"></a>Llamar al método desde código VBA  
 Ahora puede llamar al método `CreateTable` desde el código VBA del documento.  
  
> [!NOTE]  
>  En este tutorial, agregará código VBA al documento mientras se depura el proyecto. El código VBA que agregue a este documento se sobrescribirá la siguiente vez que compile el proyecto, ya que Visual Studio reemplaza el documento de la carpeta de resultados de compilación por una copia del documento de la carpeta de proyecto principal. Si desea guardar el código VBA, puede copiarlo en el documento de la carpeta del proyecto. Para obtener más información, consulta [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Para llamar al método desde código VBA  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  En la pestaña **Desarrollador** , en el grupo **Código** , haga clic en **Visual Basic**.  
  
     Se abrirá el Editor de Visual Basic.  
  
3.  En el menú **Insertar** , haga clic en **Módulo**.  
  
4.  Agregue el siguiente código al nuevo módulo.  
  
     Este código llama al método `CreateTable` en el ensamblado de personalización. La macro accede a este método mediante la propiedad `CallVSTOAssembly` del objeto `ThisDocument` . Esta propiedad se generó automáticamente al establecer la propiedad **EnableVbaCallers** anteriormente en este tutorial.  
  
    ```  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Presione F5.  
  
6.  Compruebe que se agregó una tabla nueva al documento.  
  
7.  Salga de Word sin guardar los cambios.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede obtener más información sobre cómo llamar a código en soluciones de Office desde VBA en estos temas:  
  
-   Llamar a código en una personalización de Visual C# desde VBA. Este proceso es diferente del proceso de Visual Basic. Para obtener más información, consulte [Tutorial: llamar a código desde VBA en un Visual C&#35; proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Llamar a código en un complemento de VSTO desde VBA. Para obtener más información, consulte [Tutorial: llamar a código en un complemento de VSTO desde VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Vea también  
 [Combinar personalizaciones de VBA y de nivel de documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programación de personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [How to: Expose Code to VBA in a Visual Basic Project](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Cómo: exponer código a VBA en una C Visual&#35; proyecto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Tutorial: Llamar a código desde VBA en una C Visual&#35; proyecto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  
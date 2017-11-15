---
title: Prueba de aplicaciones de SharePoint 2010 con pruebas de IU codificadas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: "30"
ms.author: douge
manager: douge
ms.openlocfilehash: d3ba0b9ce4366efd386d0b5c1b4d9c3f0094511b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Probar aplicaciones de SharePoint 2010 con pruebas de IU codificadas
Incluir pruebas de IU codificadas en una aplicación de SharePoint permite comprobar que toda la aplicación, incluidos sus controles de interfaz de usuario, funcionan correctamente. Las pruebas de IU codificadas también pueden validar valores y la lógica de la interfaz de usuario.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>¿Qué más debería saber sobre las pruebas de IU codificadas?  
 Para obtener más información sobre las ventajas de usar pruebas de IU codificadas, vea [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md) y [Comprobación de entregas continuas con Visual Studio 2012 – Capítulo 5: Automatización de las pruebas del sistema](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Notas**  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") Las pruebas de IU codificadas para las aplicaciones de SharePoint solo son compatibles con SharePoint 2010.  
  
-   ![Requisito previo](../test/media/prereq.png "Prereq") No se pueden usar controles de Visio y PowerPoint 2010 en la aplicación de SharePoint.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Crear una prueba de IU codificada para la aplicación de SharePoint  
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) para las aplicaciones de SharePoint 2010 es lo mismo que crear pruebas para otros tipos de aplicaciones. La grabación y la reproducción se admiten en todos los controles de la interfaz de edición web. La interfaz para seleccionar categorías y elementos web son todos los controles web estándar.  
  
 ![Elementos web de SharePoint](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Si se graba una acción, validar las acciones antes de generar código. Como hay varios comportamientos asociados con el desplazamiento del mouse, esta característica está activada de manera predeterminada. Tenga cuidado al quitar desplazamientos redundantes de las pruebas de IU codificadas. Puede hacerlo modificando el código de la prueba o usando el [editor de pruebas de IU codificadas](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Incluir pruebas de los controles de Office 2010 dentro de la aplicación de SharePoint  
 Para habilitar la automatización de algunos elementos web de Office 2010 en su aplicación de SharePoint, es necesario realizar algunas modificaciones mínimas en el código.  
  
> [!WARNING]
>  No se admiten controles de Visio y PowerPoint 2010.  
  
### <a name="excel-2010-cell-controls"></a>Controles de celda de Excel 2010  
 Para incluir controles de celda de Excel, hay que realizar algunos cambios en el código de la prueba de IU codificada.  
  
> [!WARNING]
>  Escribir texto en una celda de Excel, seguida de una acción de tecla de flecha, no se graba correctamente. Use el mouse para seleccionar celdas.  
  
 Si graba acciones en una celda vacía, tiene que modificar el código haciendo doble clic en la celda y, luego, realizando una operación de texto definida. Esto es necesario porque, al hacer clic en la celda, seguido de una acción de teclado, se activa `textarea` dentro de la celda. Grabar simplemente un `setvalue` en la celda vacía haría que se buscara el elemento `editbox` que no estará presente hasta que se haga clic en la celda. Por ejemplo:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Si graba acciones en una celda que no está vacía, la grabación será un poco más complicada, porque en cuanto agregue texto a una celda, se agregará un nuevo control \<div> como elemento secundario de la celda. El nuevo control \<div> contiene el texto que acaba de especificar. La grabadora necesita grabar acciones en el nuevo control \<div>, pero no puede porque el nuevo control \<div> no existirá hasta que se especifique la prueba. Tendrá que realizar los siguientes cambios en el código manualmente para acabar con este problema.  
  
1.  Vaya a la inicialización de la celda y establezca `RowIndex` y `ColumnIndex` como propiedades principales:  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Busque el elemento secundario `HtmlDiv` de la celda:  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  Agregue código para una acción de doble clic del mouse en `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Agregue código para texto establecido en `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Habilitar pruebas de IU codificadas de los elementos web de Silverlight en la aplicación de SharePoint 2010  
 Las pruebas de Silverlight no se admiten en Visual Studio 2012 y versiones posteriores. Pero, si desea probar los elementos web de Silverlight en la aplicación de SharePoint 2010, puede instalar un complemento de Silverlight independiente desde la Galería de Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Configurar el equipo  
  
1.  Asegúrese de que tiene Visual Studio 2012.1 o posterior instalado.  
  
2.  Instale el [complemento de la prueba de IU de Microsoft Visual Studio para Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3.  Instale [Fiddler](http://www.fiddler2.com/fiddler2/). Se trata simplemente de una herramienta que captura y registra el tráfico HTTP.  
  
4.  Descargue el [proyecto de fiddlerXap](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Descomprímalo, compílelo y ejecute el script "CopySLHelper.bat" para instalar la DLL auxiliar necesaria para comprobar los elementos web de Silverlight cuando use la herramienta Fiddler.  
  
 Después de configurar el equipo, haga lo siguiente para empezar a comprobar la aplicación de SharePoint 2010 con los elementos web de Silverlight:  
  
#### <a name="testing-silverlight-web-parts"></a>Probar elementos web de Silverlight  
  
1.  Inicie Fiddler.  
  
2.  Borre la memoria caché de exploración. Esto es necesario porque el archivo XAP (que contiene la DLL auxiliar de automatización de interfaz de usuario de Silverlight) se suele almacenar en caché. Tenemos que asegurarnos de que se selecciona el archivo XAP, por eso borramos la memoria caché de exploración.  
  
3.  Abra la página web.  
  
4.  Inicie la grabadora y genere código como lo haría para una prueba de aplicación web normal.  
  
5.  Es preciso confirmar que el código generado hace referencia a Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Para más información, vea [Pruebas de IU de SharePoint 2010 con Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx).  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="blogs"></a>Blogs  
 [Pruebas de IU de SharePoint 2010 con Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Descripción de la lógica de búsqueda de controles de Silverlight en la prueba de IU codificada](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Captura de la propiedad de un control de Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Índice de contenido para la prueba de IU codificada](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Orientación  
 [Comprobación de entregas continuas con Visual Studio 2012 – Capítulo 5: Automatización de las pruebas del sistema](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Foro  
 [Blog de Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Vea también  
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Rendimiento web y pruebas de carga de aplicaciones de SharePoint 2010 y 2013](/devops-test-docs/test/web-performance-and-load-testing-sharepoint-2010-and-2013-applications)   
 [Crear soluciones de SharePoint](/office-dev/office-dev/create-sharepoint-solutions)   
 [Comprobar y depurar código de SharePoint](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
 [Compilar y depurar soluciones de SharePoint](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
 [Generar perfiles de rendimiento de aplicaciones de SharePoint](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)

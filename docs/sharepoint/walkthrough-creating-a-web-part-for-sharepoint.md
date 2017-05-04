---
title: "Tutorial: Crear un elemento web para SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "elementos web [desarrollo de SharePoint en Visual Studio], crear"
  - "elementos web [desarrollo de SharePoint en Visual Studio], diseñar"
  - "elementos web [desarrollo de SharePoint en Visual Studio], desarrollar"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Tutorial: Crear un elemento web para SharePoint
  Los elementos web permiten a los usuarios modificar directamente el contenido, el aspecto y el comportamiento de las páginas de sitios de SharePoint mediante un explorador.  En este tutorial se muestra cómo crear un elemento web utilizando la plantilla **elemento web** de Visual Studio 2010.  
  
 El elemento web muestra los empleados en una cuadrícula de datos.  El usuario especifica la ubicación del archivo que contiene los datos de los empleados.  El usuario también puede filtrar la cuadrícula de datos para que en la lista solo aparezcan los empleados que son administradores.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un elemento web utilizando la plantilla **elemento web** de Visual Studio.  
  
-   Crear una propiedad que puede establecer el usuario del elemento web.  Esta propiedad especifica la ubicación del archivo de datos de los empleados.  
  
-   Presentar el contenido de un elemento web agregando controles a la colección de controles del elemento web.  
  
-   Crear un nuevo elemento de menú, al que se hace referencia como a un *verbo* que aparece en el menú de verbos del elemento web presentado.  Los verbos permiten al usuario modificar los datos que aparecen en el elemento web.  
  
-   Probar el elemento web en SharePoint.  
  
    > [!NOTE]  
    >  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté utilizando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Microsoft Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] o una edición de Visual Studio Application Lifecycle Management \(ALM\).  
  
## Crear un proyecto vacío de SharePoint  
 Primero, cree un proyecto de SharePoint vacío.  Más adelante le agregará un elemento web utilizando la plantilla **elemento web**.  
  
#### Para crear un proyecto vacío de SharePoint  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la opción **Ejecutar como administrador**.  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **SharePoint** bajo el lenguaje que desea usar y después elija el nodo **2010**.  
  
4.  En el panel **Plantillas**, elija **Proyecto de SharePoint 2010** y después elija el botón **Aceptar**.  
  
     Aparece el **Asistente para personalización de SharePoint**.  Este asistente permite seleccionar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.  
  
5.  Elija el botón de opción **Implementar como solución de granja de servidores** y después elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.  
  
## Agregar un elemento web al proyecto  
 Agregue un **elemento web** al proyecto.  El **elemento web** agrega el archivo de código.  Después, agregará código al archivo de código para presentar el contenido del elemento web.  
  
#### Para agregar un elemento web al proyecto  
  
1.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, en el panel **Plantillas instaladas**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010**.  
  
3.  En la lista de plantillas de SharePoint, elija la plantilla **Elemento web** y, a continuación, elija el botón **Agregar**.  
  
     El **elemento web** aparece en el **Explorador de soluciones**.  
  
## Presentar contenido en el elemento web  
 Puede especificar los controles que desea que aparezcan en el elemento web agregándolos a la colección de controles de la clase Web Part.  
  
#### Para presentar contenido en el elemento web  
  
1.  En el **Explorador de soluciones**, abra WebPart1.vb \(en Visual Basic\) o WebPart1.cs \(en C\#\).  
  
     Se abre el archivo de código del elemento web en el editor de código.  
  
2.  Agregue las siguientes instrucciones en la parte superior del archivo de código del elemento web.  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  Agregue el código siguiente a la clase `WebPart1`.  Este código declara los siguientes campos:  
  
    -   Una cuadrícula de datos para mostrar los empleados en el elemento web.  
  
    -   Texto que aparece en el control que se utiliza para filtrar la cuadrícula de datos.  
  
    -   Una etiqueta que presenta un error si la cuadrícula de datos no puede mostrar los datos.  
  
    -   Una cadena que contiene la ruta del archivo de datos de los empleados.  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  Agregue el código siguiente a la clase `WebPart1`.  Este código agrega una propiedad personalizada denominada `DataFilePath` al elemento web.  Una propiedad personalizada es una propiedad que el usuario puede establecer en SharePoint.  Esta propiedad obtiene y establece la ubicación de un archivo de datos XML que se utiliza para rellenar la cuadrícula de datos.  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  Reemplace el método `CreateChildControls` por el código siguiente.  Este código realiza las tareas siguientes:  
  
    -   Agrega la cuadrícula de datos y la etiqueta que declaró en el paso anterior.  
  
    -   Enlaza la cuadrícula de datos a un archivo XML que contiene los datos de los empleados.  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  Agregue el método siguiente a la clase `WebPart1`.  Este código realiza las tareas siguientes:  
  
    -   Crea un verbo que aparece en el menú de verbos de elemento web del elemento web presentado.  
  
    -   Controla el evento que se genera cuando el usuario elige el verbo del menú de verbos.  Este código filtra la lista de empleados que aparece en la cuadrícula de datos.  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## Prueba del elemento web  
 Cuando se ejecuta el proyecto, se abre el sitio de SharePoint.  El elemento web se agrega automáticamente a la Galería de elementos web de SharePoint.  Puede agregar el elemento web a cualquier página de elementos web.  
  
#### Para probar el elemento web  
  
1.  Pegue el código siguiente en un archivo de Bloc de notas.  Este archivo XML contiene los datos de ejemplo que aparecerán en el elemento web.  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  En el Bloc de notas, en la barra de menús, elija **Archivo**, **Guardar como**.  
  
3.  En el cuadro de diálogo **Guardar como**, en la lista desplegable **Guardar como tipo**, elija **Todos los archivos**.  
  
4.  En el cuadro **Nombre de archivo**, escriba data.xml.  
  
5.  Elija una carpeta utilizando el botón **Examinar carpetas** y, a continuación, elija el botón **Guardar**.  
  
6.  En Visual Studio, elija la tecla **F5**.  
  
     Se abre el sitio de SharePoint.  
  
7.  En el menú **Acciones del sitio**, elija **Más opciones**.  
  
8.  En la página **Crear**, elija el tipo **Página de elementos web** y después elija el botón **Crear**.  
  
9. En la página **Nueva página de elementos web**, dé a la página el nombre **SampleWebPartPage.aspx** y elija el botón **Crear**.  
  
     Aparece la página de elementos web .  
  
10. Seleccione cualquier zona de la página de elementos web.  
  
11. En la parte superior de la página, elija la pestaña **Insertar** y, a continuación, elija el botón **Elemento web**.  
  
12. En el panel **Categorías**, elija la carpeta **Personalizado**, elija el elemento web **WebPart1** y, a continuación, elija el botón **Agregar**.  
  
     El elemento web aparece en la página.  
  
## Probar la propiedad personalizada  
 Para rellenar la cuadrícula de datos que aparece en el elemento web, especifique la ruta de acceso del archivo XML que contiene los datos sobre cada empleado.  
  
#### Para probar la propiedad personalizada  
  
1.  Elija la flecha que aparece a la derecha del elemento web y después elija **Editar elemento web** del menú que aparece.  
  
     Un panel con las propiedades del elemento web aparece en el lado derecho de la página.  
  
2.  En el panel, expanda el nodo **Varios**, escriba la ruta de acceso del archivo XML que creó anteriormente, elija el botón **Aplicar** y, a continuación, elija el botón **Aceptar**.  
  
     Compruebe que en el elemento web aparece una lista de empleados.  
  
## Probar el verbo de elemento web  
 Muestra y oculta a los empleados que no son administradores cuando se hace clic en un elemento que aparece en el menú de verbos del elemento web.  
  
#### Para probar el verbo del elemento web  
  
1.  Elija la flecha que aparece a la derecha del elemento web y después elija **Muestra solo a los administradores** del menú que aparece.  
  
     Solo los empleados que son administradores aparecen en el elemento web.  
  
2.  Elija la flecha de nuevo y después elija **Muestra todos los empleados** del menú que aparece.  
  
     Todos los empleados aparecen en el elemento web.  
  
## Vea también  
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
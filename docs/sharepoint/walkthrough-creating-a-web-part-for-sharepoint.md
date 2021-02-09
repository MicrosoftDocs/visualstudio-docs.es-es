---
title: 'Tutorial: crear un elemento Web para SharePoint | Microsoft Docs'
description: Cree un elemento Web para SharePoint. Los elementos web permiten a los usuarios cambiar directamente el contenido, la apariencia y el comportamiento de las páginas del sitio de SharePoint mediante un explorador.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2d14bfd069fcf5064c9d8643393e28e52570be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918630"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Tutorial: Creación de un elemento web para SharePoint

Los elementos web permiten a los usuarios modificar directamente el contenido, el aspecto y el comportamiento de las páginas de sitios de SharePoint mediante un explorador. En este tutorial se muestra cómo crear un elemento Web utilizando la plantilla elemento **Web** en Visual Studio 2010.

El elemento web muestra los empleados en una cuadrícula de datos. El usuario especifica la ubicación del archivo que contiene los datos de los empleados. El usuario también puede filtrar la cuadrícula de datos para que en la lista solo aparezcan los empleados que son administradores.

En este tutorial se muestran las tareas siguientes:

- Crear un elemento Web utilizando la plantilla de elementos de elemento **Web** de Visual Studio.

- Crear una propiedad que puede establecer el usuario del elemento web. Esta propiedad especifica la ubicación del archivo de datos de los empleados.

- Presentar el contenido de un elemento web agregando controles a la colección de controles del elemento web.

- Crear un nuevo elemento de menú, denominado *verbo,* que aparece en el menú de verbos del elemento Web representado. Los verbos permiten al usuario modificar los datos que aparecen en el elemento web.

- Probar el elemento web en SharePoint.

    > [!NOTE]
    > Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos

- Ediciones compatibles de Microsoft Windows y SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Crear un proyecto vacío de SharePoint

Primero, cree un proyecto de SharePoint vacío. Más adelante, agregará un elemento Web al proyecto utilizando la plantilla elemento **Web** .

1. Empiece [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la opción **Ejecutar como administrador** .

2. En la barra de hombres, elija **archivo**  >  **nuevo**  >  **proyecto**.

3. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **SharePoint** bajo el lenguaje que desea usar y, a continuación, elija el nodo **2010** .

4. En el panel **plantillas** , elija **proyecto de SharePoint 2010** y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** . Este asistente permite seleccionar el sitio que se va a usar para depurar el proyecto, así como el nivel de confianza de la solución.

5. Elija el botón de opción **implementar como solución de granja de servidores** y, después, elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Agregar un elemento Web al proyecto

Agregue un elemento de elemento **Web** al proyecto. El elemento **Web** agrega el archivo de código del elemento Web. Después, agregará código al archivo de código para presentar el contenido del elemento web.

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , en el panel **plantillas instaladas** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

3. En la lista de plantillas de SharePoint, elija la plantilla **elemento Web** y, a continuación, elija el botón **Agregar** .

     El elemento **Web** aparece en **Explorador de soluciones**.

## <a name="rendering-content-in-the-web-part"></a>Representar el contenido en el elemento Web

Puede especificar los controles que desea que aparezcan en el elemento web agregándolos a la colección de controles de la clase Web Part.

1. En **Explorador de soluciones**, Abra *WebPart1. vb* (en Visual Basic) o *WebPart1.CS* (en C#).

     Se abre el archivo de código del elemento web en el editor de código.

2. Agregue las siguientes directivas a la parte superior del archivo de código del elemento Web.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Agregue el siguiente código a la clase `WebPart1` . Este código declara los siguientes campos:

   - Una cuadrícula de datos para mostrar los empleados en el elemento web.

   - Texto que aparece en el control que se utiliza para filtrar la cuadrícula de datos.

   - Una etiqueta que presenta un error si la cuadrícula de datos no puede mostrar los datos.

   - Una cadena que contiene la ruta del archivo de datos de los empleados.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Agregue el siguiente código a la clase `WebPart1` . Este código agrega una propiedad personalizada denominada `DataFilePath` al elemento web. Una propiedad personalizada es una propiedad que el usuario puede establecer en SharePoint. Esta propiedad obtiene y establece la ubicación de un archivo de datos XML que se utiliza para rellenar la cuadrícula de datos.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Reemplace el método `CreateChildControls` por el código siguiente. Este código realiza las tareas siguientes:

   - Agrega la cuadrícula de datos y la etiqueta que declaró en el paso anterior.

   - Enlaza la cuadrícula de datos a un archivo XML que contiene los datos de los empleados.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Agrega el método siguiente a la clase `WebPart1`: Este código realiza las tareas siguientes:

   - Crea un verbo que aparece en el menú de verbos de elemento web del elemento web presentado.

   - Controla el evento que se genera cuando el usuario elige el verbo del menú de verbos. Este código filtra la lista de empleados que aparece en la cuadrícula de datos.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Probar el elemento Web

Cuando se ejecuta el proyecto, se abre el sitio de SharePoint. El elemento web se agrega automáticamente a la Galería de elementos web de SharePoint. Puede agregar el elemento web a cualquier página de elementos web.

1. Pegue el código siguiente en un archivo de Bloc de notas. Este archivo XML contiene los datos de ejemplo que aparecerán en el elemento web.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
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

2. En el Bloc de notas, en la barra de menús, elija **archivo**  >  **Guardar como**.

3. En el cuadro de diálogo **Guardar como** , en la lista **Guardar como tipo** , elija **todos los archivos**.

4. En el cuadro **nombre de archivo** , escriba **data.xml**.

5. Elija cualquier carpeta mediante el botón **examinar carpetas** y, a continuación, elija el botón **Guardar** .

6. En Visual Studio, elija la tecla **F5** .

     Se abre el sitio de SharePoint.

7. En el menú **acciones del sitio** , elija **más opciones**.

8. En la página **crear** , elija el tipo de **Página elemento Web** y, a continuación, elija el botón **crear** .

9. En la página **nueva página de elementos Web** , asigne un nombre a la página **nombre samplewebpartpage. aspx** y, a continuación, elija el botón **crear** .

     Aparece la página de elementos web .

10. Seleccione cualquier zona de la página de elementos web.

11. En la parte superior de la página, elija la pestaña **Insertar** y, a continuación, elija el botón **elemento Web** .

12. En el panel **categorías** , elija la carpeta **personalizado** , elija el elemento Web **WebPart1** y, a continuación, elija el botón **Agregar** .

     El elemento web aparece en la página.

## <a name="test-the-custom-property"></a>Probar la propiedad personalizada

Para rellenar la cuadrícula de datos que aparece en el elemento web, especifique la ruta de acceso del archivo XML que contiene los datos sobre cada empleado.

1. Elija la flecha que aparece en el lado derecho del elemento Web y, a continuación, elija **Editar elemento Web** en el menú que aparece.

     Un panel con las propiedades del elemento web aparece en el lado derecho de la página.

2. En el panel, expanda el nodo **varios** , escriba la ruta de acceso del archivo XML que creó anteriormente, elija el botón **aplicar** y elija el botón **Aceptar** .

     Compruebe que en el elemento web aparece una lista de empleados.

## <a name="test-the-web-part-verb"></a>Prueba del verbo del elemento Web

Muestre y oculte los empleados que no son administradores seleccionando un elemento que aparece en el menú de verbos del elemento Web.

1. Elija la flecha que aparece en el lado derecho del elemento Web y, a continuación, elija **Mostrar solo administradores** en el menú que aparece.

     Solo los empleados que son administradores aparecen en el elemento web.

2. Vuelva a elegir la flecha y, a continuación, elija **Mostrar todos los empleados** en el menú que aparece.

     Todos los empleados aparecen en el elemento web.

## <a name="see-also"></a>Vea también

[Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Cómo: crear un elemento](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 Web de SharePoint [Cómo: crear un elemento Web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Tutorial: crear un elemento Web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

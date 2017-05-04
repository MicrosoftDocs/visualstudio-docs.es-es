---
title: "Tutorial: Crear una lista externa en SharePoint con datos profesionales | Microsoft Docs"
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
  - "servicio de conectividad a datos empresariales [desarrollo de SharePoint en Visual Studio]"
  - "BDC [desarrollo de SharePoint en Visual Studio], lista externa"
  - "servicio de conectividad a datos empresariales [desarrollo de SharePoint en Visual Studio], datos empresariales en una lista de SharePoint"
  - "BDC [desarrollo de SharePoint en Visual Studio], datos empresariales en una lista de SharePoint"
  - "BDC [desarrollo de SharePoint en Visual Studio], datos empresariales en un elemento web"
  - "BDC [desarrollo de SharePoint en Visual Studio], lista respaldada por entidades"
  - "servicio de conectividad a datos empresariales [desarrollo de SharePoint en Visual Studio], lista respaldada por entidades"
  - "servicio de conectividad a datos empresariales [desarrollo de SharePoint en Visual Studio], lista externa"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: Crear una lista externa en SharePoint con datos profesionales
  El servicio Conectividad a datos profesionales \(BDC\) permite a SharePoint mostrar los datos empresariales de las aplicaciones de servidor back\-end, servicios Web y bases de datos.  
  
 En este tutorial se muestra cómo crear un modelo para el servicio BDC que devuelve información sobre los contactos de una base de datos de ejemplo.  Después, creará una lista externa en SharePoint utilizando este modelo.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un proyecto.  
  
-   Agregar una entidad al modelo.  
  
-   Agregar un método Finder.  
  
-   Agregar un método Finder específico.  
  
-   Probar el proyecto.  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de Windows y SharePoint.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] o [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Acceso a la base de datos de ejemplo AdventureWorks.  Para obtener más información sobre cómo instalar la base de datos AdventureWorks, [Bases de datos de ejemplo de SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483)vea.  
  
## Crear un proyecto que contiene un modelo BDC  
  
#### Para crear un proyecto que contiene un modelo BDC  
  
1.  En la barra de menús de Visual Studio, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En **Visual C\#** o **Visual Basic**, expanda el nodo de **sharepoint** y, a continuación el elemento de **2010** .  
  
3.  En el panel de **Plantillas** , elija **SharePoint 2010 Project**, asigne al proyecto AdventureWorksTest, y elija el botón de **Aceptar** .  
  
     Aparece el **Asistente para personalización de SharePoint**.  En este asistente, puede especificar el sitio que se va a usar para depurar el proyecto y para establecer el nivel de confianza de la solución.  
  
4.  Elija el botón de opción de **Implementar como solución de granja de servidores** para establecer el nivel de confianza.  
  
5.  Elija el botón **Finalizar** para aceptar el sitio local predeterminado de SharePoint.  
  
6.  En **Explorador de soluciones**, elija el nodo de proyecto de SharePoint.  
  
7.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.  
  
8.  En el panel de **Plantillas** , elija **Modelo de conectividad a datos profesionales \(solo en una solución de granja de servidores\)**, asigne al proyecto, escriba AdventureWorksContacts y elija el botón de **Add** .  
  
## Agregar clases de acceso de datos al proyecto  
  
#### Para agregar clases de acceso de datos al proyecto  
  
1.  En la barra de menú, elija **Herramientas**, **Conectar a base de datos**.  
  
     Se abrirá el cuadro de diálogo **Agregar conexión**.  
  
2.  Agregue una conexión a la base de datos de ejemplo AdventureWorks de SQL Server.  
  
     Para obtener más información, vea [Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/es-es/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  En el **Explorador de soluciones**, elija el nodo del proyecto.  
  
4.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
5.  En el panel de **Plantillas instaladas** , elija el nodo de **datos** .  
  
6.  En el panel de **Plantillas** , elija **clases de linq to sql**.  
  
7.  En el cuadro de **Name** , especifique AdventureWorks, y elija el botón de **Add** .  
  
     Un archivo .dbml se agrega al proyecto, y Object Relational Designer.  
  
8.  En la barra de menú, elija **Visualización**, **Explorador de servidores**.  
  
9. En el **Explorador de servidores**, expanda el nodo que representa la base de datos de ejemplo AdventureWorks y, a continuación, expanda el nodo **Tables**.  
  
10. Agregue la tabla de **Póngase en contacto \(person\)** al object relational designer.  
  
     Se crea una clase de entidad, que aparece en la superficie de diseño.  La clase de entidad tiene propiedades que se asignan a las columnas de la tabla Contact \(Person\).  
  
## Quitar la entidad predeterminada del modelo BDC  
 El proyecto **Modelo de conectividad a datos profesionales** agrega una entidad predeterminado denominada Entity1 al modelo.  Quite esta entidad.  Después, agregará una nueva entidad.  Comenzar con un modelo vacío reduce el número de pasos necesarios para completar el tutorial.  
  
#### Para quitar la entidad predeterminado del modelo  
  
1.  En **Explorador de soluciones**, expanda el nodo de **BdcModel1** , y abra el archivo de BdcModel1.bdcm.  
  
2.  El archivo del modelo de Conectividad a datos profesionales se abre en el diseñador de BDC.  
  
3.  En el diseñador, abra el menú contextual para **Entity1**y, a continuación **Suprimir**.  
  
4.  En **Explorador de soluciones**, abra el menú contextual para Entity1.vb \(en Visual Basic\) o Entity1.cs \(en C\#\) y, a continuación **Suprimir**.  
  
5.  Abrir el menú contextual para Entity1Service.vb \(en Visual Basic\) o Entity1Service.cs \(en C\#\) y, a continuación **Suprimir**.  
  
## Agregar una entidad al modelo  
 Agregue una entidad al modelo.  Puede agregar entidades de Visual Studio **Cuadro de herramientas** al diseñador de BDC.  
  
#### Para agregar una entidad al modelo  
  
1.  En la barra de menús, elija **Ver**, **Cuadro de herramientas**.  
  
2.  En la pestaña de **BusinessDataConnectivity** de **Cuadro de herramientas**, agregue **Entidad** al diseñador de BDC.  
  
     La nueva entidad aparece en el diseñador.  Visual Studio agrega un archivo denominado EntityService.vb \(en Visual Basic\) o EntityService.cs \(en C\#\) al proyecto.  
  
3.  En la barra de menú, elija **Visualización**, **Propiedades**, **Ventana**.  
  
4.  En la ventana de **Propiedades** , establezca el valor de propiedad de **Name** para ponerse en contacto.  
  
5.  En el diseñador, abra el menú contextual para la entidad, elija **Add**y, a continuación **Identificador**.  
  
     Un nuevo identificador aparece en la entidad.  
  
6.  En la ventana **Propiedades**, cambie el nombre del identificador por ContactID.  
  
7.  En la lista de **Nombre de tipo** , elija **System.Int32**.  
  
## Agregar un método Finder concreto  
 Para permitir al servicio BDC mostrar un contacto concreto, debe agregar un método Finder específico.  Las llamadas al servicio BDC el método Finder específico cuando un usuario elige un elemento de una lista y elija el botón de **Vea el elemento** en la cinta de opciones.  
  
 Agregue un método Finder específico a la entidad Contact utilizando la ventana **Detalles del método de BDC**.  Para devolver una entidad concreta, agregue código al método.  
  
#### Para agregar un método Finder específico  
  
1.  En el diseñador de BDC, elija la entidad de **Contacto** .  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana Detalles del método de BDC.  
  
3.  En la lista de **Agregar un método** , elija **Crear método Finder específico**.  
  
     Visual Studio agrega los siguientes elementos al modelo.  Estos elementos aparecen en la ventana **Detalles del método de BDC**.  
  
    -   Un método denominado Readitem.  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un parámetro devuelto para el método.  
  
    -   Un descriptor de tipo para cada parámetro.  
  
    -   Una instancia de método para el método.  
  
4.  En la ventana de **Detalles del método de BDC** , abra la lista que aparece en el descriptor de **Contacto** y, a continuación **edición**.  
  
     **Explorador de BDC** Abre y proporciona una vista jerárquica del modelo.  
  
5.  En la ventana de **Propiedades** , abra la lista junto a la propiedad de **TypeName** , elija la ficha de **Proyecto actual** y, a continuación la propiedad de **Contacto** .  
  
6.  En **Explorador de BDC**, abra el menú contextual de **Contacto**y, a continuación **Agregar descriptor de tipo**.  
  
     Un nuevo descriptor denominado **TypeDescriptor1** aparece en **Explorador de BDC**.  
  
7.  En la ventana de **Propiedades** , establezca el valor de propiedad de **Name** a **ContactID**.  
  
8.  Abra la lista junto a la propiedad de **TypeName** y, a continuación **Int32**.  
  
9. Abra la lista junto a la propiedad de **Identificador** y, a continuación **ContactID**.  
  
10. Repita los pasos desde el 6 para crear un descriptor de tipos para cada uno de los siguientes campos.  
  
    |Name|Nombre de tipo|  
    |----------|--------------------|  
    |Nombre|System.String|  
    |Apellido|System.String|  
    |Teléfono|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. En el diseñador de BDC, en la entidad de **Contacto** , abra el método de **ReadItem** .  
  
     El archivo de código del servicio Contact se abre en el editor de código.  
  
12. En la clase `ContactService`, reemplace el método `ReadItem` por el código siguiente.  Este código realiza las tareas siguientes:  
  
    -   Recupera un registro de la tabla Contact de la base de datos de AdventureWorks.  
  
    -   Devuelve una entidad Contact al servicio BDC.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Agregar un método Finder  
 Para permitir que el servicio BDC muestre los contactos en una lista, debe agregar un método Finder.  Agregue un método Finder a la entidad Contact utilizando la ventana **Detalles del método de BDC**.  Para devolver una colección de entidades al servicio BDC, agregue código al método.  
  
#### Para agregar un método Finder  
  
1.  En el diseñador de BDC, elija la entidad de **Contacto** .  
  
2.  En la ventana de **Detalles del método de BDC** , contraiga el nodo de **ReadItem** .  
  
3.  En **Agregar un método** indicado en método de **ReadList** , elija **Crear método Finder**.  
  
     Visual Studio agrega un método, un parámetro devuelto y un descriptor de tipos.  
  
4.  En el diseñador de BDC, en la entidad de **Contacto** , abra el método de **ReadList** .  
  
     El archivo de código para el servicio contact se abre en el editor de código.  
  
5.  En la clase `ContactService`, reemplace el método `ReadList` por el código siguiente.  Este código realiza las tareas siguientes:  
  
    -   Recupera los datos de la tabla Contacts de la base de datos AdventureWorks.  
  
    -   Devuelve una lista de entidades Contact al servicio BDC.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Probar el proyecto  
 Al ejecutar el proyecto, se abre el sitio de SharePoint y Visual Studio agrega el modelo al servicio Conectividad a datos profesionales.  Cree una lista externa en SharePoint que haga referencia a la entidad Contact.  Los datos de los contactos de la base de datos AdventureWorks aparecen en la lista.  
  
> [!NOTE]  
>  Quizás necesite modificar la configuración de seguridad de SharePoint para poder depurar la solución.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### Para probar el proyecto  
  
1.  Elija la tecla **F5**.  
  
     Se abre el sitio de SharePoint.  
  
2.  En el menú de **Acciones del sitio** , elija el comando de **Más opciones** .  
  
3.  En la página de **crear** , elija la plantilla de **Lista externa** , y elija el botón de **crear** .  
  
4.  Asigne a la lista personalizada el nombre Contacts.  
  
5.  Elija el botón examinar situado junto al campo de **Tipo de contenido externo** .  
  
6.  En el cuadro de diálogo de **Selector externo de tipo de contenido** , elija el elemento de **AdventureWorksContacts.BdcModel1.Contact** , y elija el botón de **crear** .  
  
     SharePoint crea una lista externa que contenga los contactos de la base de datos de ejemplo AdventureWorks.  
  
7.  Para probar el método Finder específico, elija un contacto de la lista.  
  
8.  En la cinta de opciones, elija la ficha de **Elementos** , y elija el comando de **Elemento view** .  
  
     Los detalles del contacto que eligió aparecen en un formulario.  
  
## Pasos siguientes  
 En estos temas, puede obtener más información sobre cómo diseñar modelos para el servicio BDC en SharePoint:  
  
-   [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md).  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
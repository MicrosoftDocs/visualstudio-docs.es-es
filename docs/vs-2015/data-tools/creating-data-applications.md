---
title: Crear aplicaciones de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291322"
---
# <a name="creating-data-applications"></a>Crear aplicaciones de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona muchas herramientas en tiempo de diseño para crear aplicaciones que tienen acceso a datos. Esta introducción proporciona información general sobre los procesos básicos relacionados con la creación de aplicaciones que funcionan con datos. Se han omitido muchos detalles a fin de ofrecer una fuente de información general y punto de partida de las muchas otras páginas de la Ayuda relacionadas con la creación de una aplicación de datos.  
  
 A medida que desarrolla aplicaciones que tienen acceso a datos en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], deberá cumplir con diferentes requisitos. En algunos casos, puede que simplemente desee mostrar datos en un formulario. En otros, quizá necesite idear un modo de compartir información con otras aplicaciones o procesos.  
  
 Independientemente de lo que haga con los datos, hay ciertos conceptos fundamentales que debe entender. Es posible que nunca use ciertos detalles sobre manipulación de datos, por ejemplo, tal vez nunca cree una base de datos mediante programación, pero es muy útil comprender los conceptos básicos sobre datos, así como las herramientas de datos (asistentes y diseñadores) disponibles en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Una aplicación de datos típica utiliza la mayoría de los procesos que se ilustran en el diagrama siguiente:  
  
 ![Gráfico de ciclo de datos](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
El ciclo de datos  
  
 A medida que crea la aplicación, piense en la tarea que intenta lograr. Utilice las secciones siguientes que le servirán de ayuda en la búsqueda de las herramientas y los objetos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que tiene a su disposición.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona asistentes para simplificar varios de los procesos que aparecen en el diagrama anterior. Por ejemplo, ejecutar la **Asistente para configuración de origen de datos** proporciona la aplicación con la suficiente información para conectarse a los datos, crear un conjunto de datos con tipo para recibir los datos y llevar los datos a la aplicación.  
  
 Para ver rápidamente cómo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] le ayuda a desarrollar aplicaciones de datos, vea [Tutorial: crear una sencilla aplicación de datos](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Conectarse a datos  
 Para llevar datos a la aplicación (y devolver los cambios al origen de datos), debe establecerse algún tipo de comunicación bidireccional. Esta comunicación bidireccional la controlan, por lo general, los objetos de su modelo de datos.  
  
 Por ejemplo, `TableAdapter` conecta las aplicaciones que usan conjuntos de datos a una base de datos y <xref:System.Data.Objects.ObjectContext> conecta las entidades de Entity Framework a una base de datos. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona varias herramientas para ayudar para crear conexiones que pueden ser utilizadas por su aplicación. Para obtener más información sobre cómo conectar su aplicación a los datos, vea [conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Para obtener información sobre cómo usar los conjuntos de datos para conectar la aplicación a los datos en una base de datos, vea [Tutorial: conectarse a datos en una base de datos (formularios Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Preparara la aplicación para recibir datos  
 Si la aplicación usa un modelo de datos desconectado, necesita almacenar temporalmente los datos en la aplicación mientras trabaja con ella. Visual Studio proporciona herramientas de ayuda para crear los objetos que la aplicación usa para almacenar temporalmente datos: conjuntos de datos, entidades y objetos [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Una aplicación que usa un modelo de datos desconectado se conectará normalmente a una base de datos, ejecutará una consulta que lleva los datos a la aplicación, se desconectará de la base de datos y, a continuación, manipulará los datos "sin conexión" antes de volver a conectar y actualizar la base de datos.  
  
 Para obtener más información sobre la creación de conjuntos de datos con tipo en la aplicación, consulte [preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Para obtener más información sobre el uso de conjuntos de datos en aplicaciones de n niveles, vea [separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Para obtener información sobre cómo crear un conjunto de datos, complete los procedimientos de [Tutorial: crear un conjunto de datos con el Diseñador de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Para obtener información sobre cómo crear [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objetos, complete los procedimientos de [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Buscar datos en la aplicación  
 Independientemente de que la aplicación utilice un modelo de datos desconectado, necesitará obtener datos. Lleve los datos a la aplicación mediante la ejecución de consultas o procedimientos almacenados de una base de datos. Las aplicaciones que almacenan datos en conjuntos de datos ejecutan consultas y procedimientos almacenados mediante el uso de `TableAdapter`s, mientras que las aplicaciones que almacenan datos en entidades ejecutan las consultas mediante [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) o conectando las entidades directamente a los procedimientos almacenados. Para obtener más información sobre cómo crear y modificar consultas que usan TableAdapters, vea [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) y [Cómo: editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Para obtener más información sobre cómo cargar datos en conjuntos de datos y cómo ejecutar consultas y procedimientos almacenados, vea [capturar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 Para obtener información sobre cómo cargar datos en un conjunto de datos, complete los procedimientos de [Tutorial: mostrar datos en un formulario de Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) y examine el código en el controlador de eventos de carga del formulario.  
  
 Para obtener información sobre cómo cargar datos en [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] objetos, complete los procedimientos de [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Para obtener información sobre cómo crear y ejecutar una consulta SQL, consulte [Cómo: crear y ejecutar una instrucción SQL que devuelve las filas](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Para obtener información sobre cómo ejecutar un procedimiento almacenado, vea [Cómo: ejecutar un procedimiento almacenado que devuelve las filas](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Mostrar datos en formularios  
 Después de introducir los datos en la aplicación, los mostrará en un formulario para que los usuarios los vean o los modifiquen. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), donde puede arrastrar elementos a formularios para crear automáticamente controles enlazados a datos que muestran datos. Para obtener más información sobre el enlace de datos y mostrarlos a los usuarios, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Para obtener información sobre cómo presentar datos a los usuarios, complete los procedimientos de los siguientes tutoriales (preste especial atención al proceso de arrastrar elementos desde el **orígenes de datos** ventana):  
  
-   [Tutorial: Mostrar datos en un formulario Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Tutorial: Enlazar controles de Silverlight a un servicio de datos WCF](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Modificar datos en la aplicación  
 Cuando ya ha presentado los datos a los usuarios, es probable que los modifiquen agregando, cambiando y eliminando registros antes de devolverlos a la base de datos.  
  
 Para obtener más información sobre cómo trabajar con los datos una vez que se carga en el conjunto de datos, vea [modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Validar datos  
 Al realizar cambios en los datos, es posible que desee comprobar los cambios antes de permitir que los valores sean aceptados de regreso en la base de datos o que éstos se escriban en ella. *Validación* es el nombre del proceso para comprobar que estos nuevos valores son aceptables para los requisitos de la aplicación. Puede agregar lógica para comprobar los valores de la aplicación a medida que se modifican.  Visual Studio proporciona herramientas de ayuda para agregar código que valida los datos durante los cambios de columnas y filas. Para obtener más información, consulte [validar datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Para obtener información sobre cómo agregar validación de datos a la aplicación, consulte [Tutorial: agregar validación a un conjunto de datos](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Para obtener información sobre cómo agregar validación a un conjunto de datos que se divide en una aplicación de n niveles, vea [agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Guardado de datos  
 Después de realizar los cambios en la aplicación (y validarlos), es posible que desee enviar los cambios a la base de datos. Las aplicaciones que almacenan datos en conjuntos de datos normalmente usan un TableAdapterManager para guardar los datos. Para obtener más información, consulte [información general sobre TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Las aplicaciones de Entity Framework usan la <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> método para guardar los datos.  
  
 Para obtener más información sobre cómo devolver datos actualizados a una base de datos, vea [guardar datos](../data-tools/saving-data.md).  
  
 Para obtener información sobre cómo enviar datos actualizados de un conjunto de datos a una base de datos, complete los procedimientos de [Tutorial: guardar datos de tablas de datos relacionadas (actualización jerárquica)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Temas relacionados  
 [Introducción a las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Proporciona vínculos a temas en los que se aborda la creación de aplicaciones que trabajan con datos.  
  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Proporciona vínculos a temas sobre cómo usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para conectar la aplicación a datos y crear orígenes de datos para las aplicaciones.  
  
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Proporciona vínculos a temas que explican cómo trabajar con modelos de datos en una aplicación, incluidos los conjuntos de datos y Entity Data Model.  
  
 [Obtener datos en la aplicación](../data-tools/fetching-data-into-your-application.md)  
 Proporciona vínculos a temas que describen cómo cargar datos en la aplicación.  
  
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Proporciona vínculos a temas que explican cómo enlazar controles de Windows Forms, WPF y Silverlight a orígenes de datos.  
  
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)  
 Proporciona vínculos a temas que describen cómo cambiar datos en la aplicación.  
  
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Proporciona vínculos a temas que describen cómo agregar validación a los cambios de datos.  
  
 [Guardar datos](../data-tools/saving-data.md)  
 Proporciona vínculos a temas que explican cómo enviar datos actualizados de una aplicación a una base de datos o cómo guardarlos en otros formatos, por ejemplo, XML.  
  
 [Herramientas para trabajar con orígenes de datos en Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Proporciona vínculos a temas acerca de las herramientas que puede usar para trabajar con orígenes de datos en Visual Studio, como el **orígenes de datos** ventana y ADO.NET Entity Data Model Designer.
---
title: 'Cómo: conectarse a datos en una base de datos | Microsoft Docs'
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
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273811"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Cómo: Conectarse a los datos de una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar Visual Studio para conectar una aplicación con una base de datos. Después de crear la conexión de datos, Visual Studio genera un modelo de datos que su aplicación utiliza para interactuar con los datos de la base de datos. Los objetos del modelo de datos aparecen en la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). A continuación, puede crear controles enlazados a datos arrastrando elementos desde la **ventana Orígenes de datos** a una superficie de diseño. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 En este tema se proporcionan las instrucciones para conectarse a una base de datos y crear los siguientes tipos de modelos de datos:  
  
-   Conjunto de datos  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  También puede utilizar Visual Studio para crear las clases LINQ to SQL a partir de una base de datos. Sin embargo, clases LINQ to SQL no aparecen en la **orígenes de datos** ventana y no se pueden arrastrar directamente a un diseñador para crear controles enlazados a datos. Para obtener más información sobre la creación de LINQ a las clases SQL desde una base de datos, vea [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Conectarse a una base de datos y crear un conjunto de datos  
 Al crear un conjunto de datos basado en una base de datos, Visual Studio crea un conjunto de clases que representan una vista programable de los datos. La clase principal se denomina un *con el tipo de conjunto de datos*. El conjunto de datos con tipo contiene objetos de tabla de datos que representan las tablas en la base de datos. Para obtener más información acerca de los conjuntos de datos con tipo, consulte [herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Después de crear un conjunto de datos, puede crear controles Windows Forms o WPF enlazados a datos arrastrando los objetos del conjunto de datos de la ventana Orígenes de datos al diseñador de Windows Forms o de WPF.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Para conectar la aplicación a una base de datos y crear un conjunto de datos  
  
1.  Abra un proyecto existente en Visual Studio o cree un nuevo proyecto.  
  
2.  En el menú **Datos** , haga clic en **Agregar nuevo elemento**.  
  
     El **Asistente para configuración de origen de datos** se abre.  
  
3.  En el **elegir un tipo de origen de datos** página, seleccione **base de datos**y, a continuación, haga clic en **siguiente**.  
  
4.  En el **elegir un modelo de base de datos** página, seleccione **Dataset**y, a continuación, haga clic en **siguiente**.  
  
5.  En el **elegir la conexión de datos** , seleccione una conexión de datos de la lista de conexiones disponibles y, a continuación, haga clic en **siguiente**.  
  
     Si la conexión de datos deseada no está disponible, cree una nueva conexión siguiendo los pasos descritos en [crear una nueva conexión de base de datos](#CreatingDataConnection).  
  
6.  En el **Guardar cadena de conexión en el archivo de configuración de aplicación** página, opcionalmente desactive el **Sí, guardar la conexión como** casilla de verificación si desea guardar la cadena de conexión directamente en compilado aplicación. De forma predeterminada, la conexión se guarda en el archivo de configuración de la aplicación. Para obtener más información, consulte [Cómo: guardar y editar las cadenas de conexión](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  En el **elija los objetos de base de datos** página, seleccione los objetos de base de datos que va a utilizar en la aplicación. También tiene la opción de reemplazar el valor predeterminado **nombre de conjunto de datos**.  
  
8.  Haga clic en **Finalizar**. Ahora está disponible en el conjunto de datos que acaba de crear el **orígenes de datos** ventana.  
  
    > [!NOTE]
    >  Si el **orígenes de datos** ventana no está abierta, haga clic en **Mostrar orígenes de datos** en el **datos** menú para abrir la ventana.  
  
9. Ahora puede arrastrar elementos desde el **orígenes de datos** ventana hasta WPF designer, el Diseñador de Windows Forms, o la [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) para crear controles enlazados a datos. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Conectarse a la base de datos y crear un Entity Data Model  
 Al crear un Entity Data Model basado en una base de datos, Visual Studio crea un conjunto de clases que representan una vista programable de los datos. Para obtener más información acerca de Entity Data Models y ADO.NET Entity Framework, vea [Introducción a Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Después de crear un Entity Data Model, puede crear los controles WPF enlazados a datos arrastrando los objetos entidad de la ventana Orígenes de datos al diseñador WPF.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Para conectar la aplicación a una base de datos y crear un Entity Data Model  
  
1.  Abra un proyecto existente en Visual Studio o cree un nuevo proyecto.  
  
2.  Siga los pasos descritos en la **Asistente para Entity Data Model** para conectarse a una base de datos y especificar el contenido del modelo. Para obtener más información, consulte [Cómo: crear un nuevo archivo .edmx](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Después de completar la **Asistente para Entity Data Model**, se abre el Entity Data Model que creó en el Entity Data Model Designer y los objetos de datos están ahora disponibles en el **orígenes de datos** ventana.  
  
    > [!NOTE]
    >  Si el **orígenes de datos** ventana no está abierta, haga clic en **Mostrar orígenes de datos** en el **datos** menú para abrir la ventana.  
  
4.  Si el diseñador WPF está abierto, ahora puede arrastrar elementos desde el **orígenes de datos** ventana al diseñador para crear controles que se enlazan al Entity Data Model. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Si el Diseñador de Windows Forms está abierto, no se puede arrastrar elementos desde el **orígenes de datos** al diseñador. Para crear controles que se enlazan al Entity Data Model, debe compilar el proyecto, agregar un nuevo origen de datos de objeto basado en el Entity Data Model y, a continuación, arrastrar esos objetos al diseñador.  
  
##  <a name="CreatingDataConnection"></a> Crear una nueva conexión de base de datos  
 Cuando se usa el **Asistente para configuración de origen de datos**o **Asistente para Entity Data Model**, debe especificar una conexión a la base de datos que desea usar. Si aún no tiene una conexión, siga estos pasos para crearla.  
  
 Estas instrucciones se supone que ya ha iniciado la **Asistente para configuración de origen de datos** o **Asistente para Entity Data Model** como se describe en [conectarse a la base de datos y crear un conjunto de datos ](#dataset) y [conectarse a la base de datos y crear un Entity Data Model](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Para crear una nueva conexión a una base de datos  
  
1.  En el **elegir la conexión de datos** página de la **Asistente para configuración de origen de datos** o **Asistente para Entity Data Model**, haga clic en **nueva conexión**.  
  
     Se produce una de las acciones siguientes:  
  
    -   Si ya ha creado una conexión de datos en Visual Studio, el **Agregar conexión** abre el cuadro de diálogo.  
  
    -   Si se trata de la primera conexión de datos que ha creado en Visual Studio, el **Elegir origen de datos** muestra el cuadro de diálogo. Seleccione el tipo de base de datos que desea conectarse y, a continuación, haga clic en **Aceptar** para mostrar el **Agregar conexión** cuadro de diálogo.  
  
2.  En el **Agregar conexión** diálogo cuadro, escriba la información solicitada. El **Agregar conexión** es diferente para cada tipo de proveedor de datos de cuadro de diálogo.  
  
    > [!NOTE]
    >  Si el texto seleccionado **origen de datos** en el **Agregar conexión** cuadro de diálogo no es el origen de datos que desea conectarse, haga clic en **cambio** para abrir el **datos modificados Origen** diálogo cuadro y, a continuación, elija un origen de datos diferente.  
  
3.  En el **Agregar conexión** cuadro de diálogo, haga clic en **Aceptar**.  
  
     Vuelva a la **elegir la conexión de datos** página de la **Asistente para configuración de origen de datos** o **Asistente para Entity Data Model**.  
  
4.  En el **elegir la conexión de datos** página, asegúrese de que la conexión de datos está seleccionada y, a continuación, haga clic en **siguiente**.  
  
5.  Complete los pasos restantes el **Asistente para configuración de origen de datos** o **Asistente para Entity Data Model**.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Almacenar información confidencial, como una contraseña, puede afectar la seguridad de la aplicación. El uso de la autenticación de Windows (también conocida como seguridad integrada) es un modo más seguro de controlar el acceso a una base de datos. Para más información, consulte [Proteger la información de conexión](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Vea también  
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Conexión a un origen de datos](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)
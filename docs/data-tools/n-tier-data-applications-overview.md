---
title: "Informaci&#243;n general sobre aplicaciones de datos con n capas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "capa de datos"
  - "capa intermedia"
  - "aplicaciones con n capas, acerca de las aplicaciones con n capas"
  - "capa de presentación"
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre aplicaciones de datos con n capas
Las aplicaciones de datos con *n niveles* son aplicaciones de datos que se dividen en varios *niveles*.  Las aplicaciones con n niveles, también denominadas "aplicaciones distribuidas" o "aplicaciones multinivel", dividen el procesamiento en niveles independientes que se distribuyen entre el cliente y el servidor.  Al desarrollar aplicaciones que tienen acceso a datos, se debe realizar una separación clara entre los distintos niveles que constituyen la aplicación.  
  
 Una aplicación típica con n niveles incluye un nivel de presentación, un nivel intermedio y una capa de datos.  La manera más fácil de separar los distintos niveles de una aplicación con n niveles es creando proyectos independientes para cada nivel que se desee incluir en la aplicación.  Por ejemplo, el nivel de presentación podría ser una aplicación de formularios Windows Forms, mientras que la lógica de acceso a datos podría ser una biblioteca de clases ubicada en el nivel intermedio.  Además, el nivel de presentación podría comunicarse con la lógica de acceso a datos del nivel intermedio a través de un servicio como un servicio.  Al separar los componentes de la aplicación en niveles independientes, se aumenta la facilidad de  mantenimiento y la escalabilidad de la aplicación.  Esto se consigue mediante una integración más sencilla de nuevas tecnologías, que se pueden aplicar a un solo nivel sin necesidad de volver a diseñar la solución completa.  Además, las aplicaciones con n niveles almacenan normalmente la información confidencial en el nivel intermedio, lo cual mantiene su aislamiento respecto del nivel de presentación.  
  
 Visual Studio contiene varias características que ayudan a los programadores a crear aplicaciones con n niveles:  
  
-   El [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) ofrece una propiedad **DataSet Project** que permite separar el conjunto de datos \(capa de entidad de datos\) y `TableAdapter`s \(capa de acceso a datos\) en proyectos adicionales.  
  
-   El [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporciona los valores de configuración para generar el contexto de datos \(DataContext\) y las clases de datos en espacios de nombres independientes.  Con ello se habilita la separación lógica del acceso a datos y los niveles de entidad de datos.  
  
-   [LINQ a SQL](../Topic/LINQ%20to%20SQL.md) proporciona el método <xref:System.Data.Linq.Table%601.Attach%2A>, que permite reunir el contexto de datos de diferentes niveles en una aplicación.  Para obtener más información, vea [Aplicaciones remotas y de n niveles con LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md).  
  
## Nivel de presentación  
 El *nivel de presentación* es el nivel en el que los usuarios interactúan con una aplicación.  Normalmente, contiene también la lógica adicional de la aplicación.  Los componentes típicos del nivel de presentación son los siguientes:  
  
-   Los componentes de enlace de datos, tales como <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Las representaciones de objeto de los datos, tales como clases de entidad de [LINQ a SQL](../Topic/LINQ%20to%20SQL.md) para su uso en el nivel de presentación.  
  
 El nivel de presentación normalmente obtiene acceso al nivel intermedio mediante una referencia al servicio \(por ejemplo, una aplicación [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)\).  El nivel de presentación no obtiene acceso directamente a la capa de datos.  El nivel de presentación se comunica con la capa de datos por medio del componente de acceso a datos en el nivel intermedio.  
  
## Nivel intermedio  
 El *nivel intermedio* es la capa que el nivel de presentación y la capa de datos utilizan para comunicarse entre sí.  Los componentes típicos del nivel intermedio son los siguientes:  
  
-   La lógica empresarial \(reglas empresariales, validación de datos, etc.\).  
  
-   La lógica y los componentes de acceso a datos, como los siguientes:  
  
    -   [TableAdapters](../Topic/TableAdapters.md) y [DataAdapters y DataReaders](../Topic/DataAdapters%20and%20DataReaders.md).  
  
    -   Representaciones de objeto de los datos, como las clases de entidad de [LINQ a SQL](../Topic/LINQ%20to%20SQL.md).  
  
    -   Los servicios de aplicación comunes, como autenticación, autorización y personalización.  
  
 Las ilustraciones siguientes muestran las características y tecnologías que se encuentran disponibles en Visual Studio y dónde podrían integrarse en el nivel intermedio de una aplicación con n niveles.  
  
 ![Componentes de nivel intermedio](../data-tools/media/ntiermid.png "NtierMid")  
Nivel intermedio  
  
 El nivel intermedio se conecta normalmente con la capa de datos mediante una conexión de datos.  Esta conexión de datos está almacenada normalmente en el componente de acceso a datos.  
  
## Capa de datos  
 La *capa de datos* es básicamente el servidor que almacena los datos de una aplicación \(por ejemplo, un servidor que ejecuta [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]\).  
  
 Las ilustraciones siguientes muestran las características y tecnologías que se encuentran disponibles en Visual Studio y dónde podrían integrarse en la capa de datos de una aplicación con n niveles.  
  
 ![Componentes de capa de datos](../data-tools/media/ntierdatatier.png "ntierdatatier")  
Capa de datos  
  
 No se puede obtener acceso a la capa de datos directamente desde el cliente en el nivel de presentación.  En su lugar, el componente de acceso a datos en el nivel intermedio se utiliza para la comunicación entre las capas de datos y la presentación.  
  
## Ayuda para el desarrollo con n niveles  
 En los temas siguientes se ofrece información sobre cómo trabajar con aplicaciones de n niveles.  
  
 [Cómo: Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
  
 [Tutorial: Agregar validación a una aplicación de datos con n niveles](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
  
 [Aplicaciones remotas y de n niveles con LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)  
  
## Vea también  
 <xref:System.Data.Linq.ITable.Attach%2A>   
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)   
 [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
---
title: "C&#243;mo: Rellenar documentos con datos de servicios | Microsoft Docs"
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
helpviewer_keywords: 
  - "documentos [desarrollo de Office en Visual Studio], rellenar con datos"
  - "servicios web [desarrollo de Office en Visual Studio], rellenar con datos"
  - "datos [desarrollo de Office en Visual Studio], agregar a documentos"
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# C&#243;mo: Rellenar documentos con datos de servicios
  El acceso a los datos funciona de la misma manera en los proyectos de nivel de documento de Microsoft Office Word y en los proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para llevar los datos a la solución; además, también es posible usar controles de Windows Forms para que se muestren los datos. Asimismo, puede aprovechar los controles denominados host, ya que son objetos nativos de Microsoft Office Excel y de Microsoft Office Word mejorados con eventos y capacidad de enlace de datos. Para obtener más información, consulta [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 En el ejemplo siguiente se muestra cómo agregar controles que están enlazados a los datos, a documentos en tiempo de diseño. Para obtener un ejemplo que muestre cómo agregar controles que están enlazados a los datos a complementos VSTO en tiempo de ejecución, consulte [Tutorial: Establecer enlaces a datos de un servicio en un proyecto de complemento VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Dispone de una demostración en vídeo relacionada con este tema en [Cómo puedo interactuar con los servicios web de Microsoft Excel](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### Rellenar un proyecto de nivel de documento con los datos de un servicio web  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos de servicio para el proyecto. Para obtener más información, consulta [Cómo: Conectarse a los datos en un servicio](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Service.md).  
  
2.  Arrastre el campo o la tabla que desee desde la ventana **Orígenes de datos** al documento.  
  
     Se crea un control en el documento; esto es, un <xref:System.Windows.Forms.BindingSource> se enlaza a la clase del objeto en el proyecto y se generan las clases para el servicio.  
  
3.  En el código, cree una instancia de la clase de servicio web con la que se conectó en el paso 1.  
  
4.  Si hay propiedades que son necesarias para la comunicación con el servicio web, cree instancias de esas propiedades.  
  
5.  Cree y envíe una solicitud de datos mediante los métodos expuestos por el servicio web y las instancias de las propiedades que creó en el paso 4.  
  
     Los métodos que utilice dependerán de lo que ofrezca el servicio web.  
  
6.  Asigne los datos de respuesta del servicio web a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
 Cuando ejecute el proyecto, los controles mostrarán el primer registro del origen de datos. Puede habilitar el desplazamiento por los registros si controla los eventos Currency que usan los objetos en <xref:System.Windows.Forms.BindingSource>.  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  
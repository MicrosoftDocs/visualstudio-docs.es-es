---
title: "Configurar referencia de servicio (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "Servicios WCF, cuadro de diálogo Configurar referencia de servicio"
  - "referencias de servicio [Visual Studio], configurar comportamiento"
  - "Configurar referencia de servicio (cuadro de diálogo)"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configurar referencia de servicio (Cuadro de di&#225;logo)
El cuadro de diálogo **Configurar referencia de servicio** permite configurar el comportamiento de los servicios [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)].  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para acceder al cuadro de diálogo **Configurar referencia de servicio**, haga clic con el botón secundario en una referencia de servicio en el **Explorador de soluciones** y elija **Configurar referencia de servicio**.  También puede acceder al cuadro de diálogo haciendo clic en el botón **Avanzadas** en el [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Lista de tareas  
  
-   Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en el campo **Dirección**.  
  
-   Para cambiar el nivel de acceso de las clases de un cliente de WCF, seleccione una palabra clave de nivel de acceso en la lista **Nivel de acceso de las clases generadas**.  
  
-   Para llamar a los métodos de un servicio WCF asincrónicamente, active la casilla **Generar operaciones asincrónicas**.  
  
-   Para generar tipos de contrato de mensaje en un cliente de WCF, active la casilla **Generar siempre contratos de mensaje**.  
  
-   Para especificar tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en las listas **Tipo de colección** y **Tipo de colección de diccionario**.  
  
-   Para deshabilitar el uso compartido de tipos, desactive la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**.  Para habilitar el uso compartido de tipos para un subconjunto de ensamblados a los que se hace referencia, active la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**, seleccione **Volver a usar tipos en los ensamblados especificados** y seleccione las referencias deseadas en la lista **Ensamblados a los que se hace referencia**.  
  
## Lista de UIElement  
 **Dirección**  
 Se usa para actualizar la dirección web en la que una referencia de servicio busca un servicio.  Por ejemplo, durante el desarrollo un servicio podría hospedarse en un servidor de desarrollo para más adelante moverse a un servidor de producción, lo que hace necesario un cambio de dirección.  
  
> [!NOTE]
>  El elemento Dirección no está disponible cuando el cuadro de diálogo **Configurar referencia de servicio** se muestra desde el [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
 **Nivel de acceso para clases generadas**  
 Determina el nivel de acceso del código para clases de cliente de WCF.  
  
> [!NOTE]
>  En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar.  Para obtener más información, consulte [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
 **Generar operaciones asincrónicas**  
 Determina si se llamará a los métodos de servicio de WCF sincrónicamente \(valor predeterminado\) o asincrónicamente.  
  
 **Generar operaciones basadas en tareas**  
 Al escribir código asincrónico, esta opción permite aprovechar las ventajas de la biblioteca TPL, incorporada en .Net 4.  Consulte [Biblioteca de procesamiento paralelo basado en tareas \(TPL\)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Generar siempre contratos de mensaje**  
 Determina si se generarán tipos de contrato de mensaje para un cliente de WCF.  Para obtener más información acerca de los contratos de mensaje, consulte [Usar contratos de mensaje](../Topic/Using%20Message%20Contracts.md).  
  
 **Tipo de colección**  
 Especifica el tipo de colección de lista para un cliente de WCF.  El tipo predeterminado es <xref:System.Array>.  
  
 **Tipo de colección de diccionario**  
 Especifica el tipo de colección de diccionario para un cliente de WCF.  El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Volver a usar tipos en ensamblados a los que se hace referencia**  
 Determina si un cliente de WCF intentará volver a usar tipos que ya existen en ensamblados a los que se hace referencia en lugar de generar nuevos tipos cuando se agrega o se actualiza un servicio.  Esta opción se encuentra activada de forma predeterminada.  
  
 **Volver a usar tipos en todos los ensamblados a los que se hace referencia**  
 Cuando está seleccionada, se volverán a usar todos los tipos de la lista **Ensamblados a los que se hace referencia** si es posible.  Esta opción se encuentra activada de forma predeterminada.  
  
 **Volver a usar tipos en los ensamblados especificados**  
 Cuando está seleccionada, solo se volverán a usar los tipos seleccionados en la lista **Ensamblados a los que se hace referencia**.  
  
 **Ensamblados a los que se hace referencia**  
 Contiene una lista de los ensamblados a los que se hace referencia en el proyecto o sitio web.  Cuando **Volver a usar tipos en los ensamblados especificados** está activada, se pueden seleccionar o deseleccionar ensamblados individuales.  
  
 **Agregar referencia web**  
 Se abrirá el [Agregar referencia Web \(Cuadro de diálogo\)](http://msdn.microsoft.com/es-es/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Esta opción solo debe usarse para proyectos destinados a la versión 2.0 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  El botón **Agregar referencia web** solo está disponible cuando el cuadro de diálogo **Configurar referencia de servicio** se muestra desde el [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Vea también  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio](../data-tools/configure-service-reference-dialog-box.md)   
 [Ejemplo Consuming ASMX and WCF Services](http://msdn.microsoft.com/es-es/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)
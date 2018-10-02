---
title: Configurar el cuadro de diálogo de referencia de servicio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 60a1c7a057495b89aa8923d424fb09d9ecb1c232
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574286"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cuadro de diálogo Configurar referencia de servicio](https://docs.microsoft.com/visualstudio/data-tools/configure-service-reference-dialog-box).  
  
  
El **configurar referencia de servicio** cuadro de diálogo le permite configurar el comportamiento de [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] servicios.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para tener acceso a la **configurar referencia de servicio** cuadro de diálogo, haga un servicio hace referencia en **el Explorador de soluciones** y elija **configurar referencia de servicio**. También puede acceder haciendo clic en el cuadro de diálogo el **avanzadas** situado en la **Add Service Reference Dialog Box**.  
  
## <a name="task-list"></a>Lista de tareas  
  
-   Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en la **dirección** campo.  
  
-   Para cambiar el nivel de acceso para las clases en un cliente de WCF, seleccione una palabra clave de nivel de acceso en el **tener acceso a nivel de las clases generadas** lista.  
  
-   Para llamar a los métodos de un servicio WCF de forma asincrónica, seleccione el **generar operaciones asincrónicas** casilla de verificación.  
  
-   Para generar tipos de contrato de mensaje en un cliente de WCF, seleccione el **generar siempre contratos de mensaje** casilla de verificación.  
  
-   Para especificar los tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en el **tipo de colección** y **tipo de colección de diccionario** enumera.  
  
-   Para deshabilitar el uso compartido de tipos, desactive la **volver a usar tipos en ensamblados de referencia** casilla de verificación. Para habilitar el uso compartido para un subconjunto de ensamblados de referencia de tipos, seleccione el **volver a usar tipos en ensamblados de referencia** casilla **reutilizar tipos en los ensamblados especificados**y seleccione el elemento hace referencia en el **lista de ensamblados de referencia**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Dirección**  
 Se usa para actualizar la dirección web en la que una referencia de servicio busca un servicio. Por ejemplo, durante el desarrollo un servicio podría hospedarse en un servidor de desarrollo para más adelante moverse a un servidor de producción, lo que hace necesario un cambio de dirección.  
  
> [!NOTE]
>  El elemento dirección no está disponible cuando el **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **Add Service Reference Dialog Box**.  
  
 **Nivel de acceso para clases generadas**  
 Determina el nivel de acceso del código para clases de cliente de WCF.  
  
> [!NOTE]
>  En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, consulte [solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).  
  
 **Generar operaciones asincrónicas**  
 Determina si se llamará a los métodos de servicio de WCF sincrónicamente (valor predeterminado) o asincrónicamente.  
  
 **Generar operaciones basadas en tareas**  
 Al escribir código asincrónico, esta opción permite aprovechar las ventajas de la biblioteca TPL, incorporada en .Net 4. Consulte [biblioteca TPL (TPL)](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Generar siempre contratos de mensaje**  
 Determina si se generarán tipos de contrato de mensaje para un cliente de WCF. Para obtener más información acerca de los contratos de mensaje, consulte [Using Message Contracts](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Tipo de colección**  
 Especifica el tipo de colección de lista para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.  
  
 **Tipo de colección de diccionario**  
 Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Volver a usar tipos en ensamblados de referencia**  
 Determina si un cliente de WCF intentará volver a usar tipos que ya existen en ensamblados a los que se hace referencia en lugar de generar nuevos tipos cuando se agrega o se actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.  
  
 **Reutilizar tipos en todos los ensamblados que se hace referencia**  
 Cuando se selecciona, todos los tipos en el **lista de ensamblados de referencia** volverá a usar si es posible. Esta opción se encuentra activada de forma predeterminada.  
  
 **Reutilizar tipos en los ensamblados especificados**  
 Cuando se selecciona, solo los tipos seleccionados en el **lista de ensamblados de referencia** volverá a usar.  
  
 **Lista de ensamblados de referencia**  
 Contiene una lista de los ensamblados a los que se hace referencia en el proyecto o sitio web. Cuando **reutilizar tipos en los ensamblados especificados** está activada, los ensamblados individuales pueden estar activados o desactivados.  
  
 **Agregar referencia Web**  
 Muestra el [NIB: cuadro de diálogo de referencia Web agregar](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Esta opción solo debe usarse para proyectos destinados a la versión 2.0 de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  El **Agregar referencia Web** botón solo está disponible cuando el **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **Add Service Reference Dialog Box**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar, actualizar o quitar una referencia de servicio](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Cómo: agregar una referencia a un servicio Web](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF](../data-tools/configure-service-reference-dialog-box.md)


---
title: Cuadro de diálogo Configurar referencia de servicio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651112"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El cuadro de diálogo **configurar referencia de servicio** le permite configurar el comportamiento de [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Services.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Para acceder al cuadro de diálogo **Configurar referencia de servicio**, haga clic con el botón derecho en una referencia de servicio en el **Explorador de soluciones** y elija **Configurar referencia de servicio**. También puede acceder al cuadro de diálogo haciendo clic en el botón **Avanzadas** en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="task-list"></a>Lista de tareas

- Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en el campo **Dirección**.

- Para cambiar el nivel de acceso de las clases de un cliente de WCF, seleccione una palabra clave de nivel de acceso en la lista **Nivel de acceso de las clases generadas**.

- Para llamar a los métodos de un servicio WCF asincrónicamente, active la casilla **Generar operaciones asincrónicas**.

- Para generar tipos de contrato de mensaje en un cliente de WCF, active la casilla **Generar siempre contratos de mensaje**.

- Para especificar tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en las listas **Tipo de colección** y **Tipo de colección de diccionario**.

- Para deshabilitar el uso compartido de tipos, desactive la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**. Para habilitar el uso compartido de tipos para un subconjunto de ensamblados a los que se hace referencia, active la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**, seleccione **Volver a usar tipos en los ensamblados especificados** y seleccione las referencias deseadas en la lista **Ensamblados a los que se hace referencia**.

## <a name="uielement-list"></a>Lista de UIElement
 **Dirección** de Se utiliza para actualizar la dirección web en la que una referencia de servicio busca un servicio. Por ejemplo, durante el desarrollo un servicio podría hospedarse en un servidor de desarrollo para más adelante moverse a un servidor de producción, lo que hace necesario un cambio de dirección.

> [!NOTE]
> El elemento Dirección no está disponible cuando el cuadro de diálogo **Configurar referencia de servicio** se muestra desde el **cuadro de diálogo Agregar referencia de servicio**.

 **Nivel de acceso para clases generadas** Determina el nivel de acceso del código para las clases de cliente de WCF.

> [!NOTE]
> En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, consulte [solución de problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

 **Generar operaciones asincrónicas** Determina si los métodos de servicio de WCF se llamarán sincrónicamente (el valor predeterminado) o de forma asincrónica.

 **Generar operaciones basadas en tareas** Al escribir código asincrónico, esta opción permite aprovechar las ventajas de la biblioteca TPL (Task Parallel Library) que se presentó con .net 4. Vea [biblioteca de procesamiento paralelo de tareas (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Generar siempre contratos de mensaje** Determina si los tipos de contrato de mensaje se generarán para un cliente de WCF. Para obtener más información sobre los contratos de mensajes, vea [usar contratos de mensaje](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Tipo de colección** Especifica el tipo de colección de listas para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.

 **Tipo de colección de diccionario** Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.

 **Volver a usar tipos en ensamblados a los que se hace referencia** Determina si un cliente de WCF intentará volver a usar que ya existe en los ensamblados a los que se hace referencia, en lugar de generar nuevos tipos cuando se agrega o actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.

 **Reutilizar tipos en todos los ensamblados a los que se hace referencia** Cuando se selecciona, todos los tipos de la **lista de ensamblados a los que se hace referencia** se volverán a usar si es posible. Esta opción se encuentra activada de forma predeterminada.

 **Volver a usar tipos en ensamblados de referencia especificados** Cuando se selecciona esta opción, solo se volverán a usar los tipos seleccionados en la **lista ensamblados a los que se hace referencia** .

 **Lista de ensamblados a los que se hace referencia** Contiene una lista de ensamblados a los que se hace referencia para el proyecto o el sitio Web. Cuando se selecciona **volver a usar tipos en los ensamblados de referencia especificados** , se pueden seleccionar o borrar ensamblados individuales.

 **Agregar referencia Web** Muestra el [cuadro de diálogo NIB: Agregar referencia Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Esta opción solo debe usarse para proyectos destinados a la versión 2.0 de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

> [!NOTE]
> El botón **Agregar referencia Web** solo está disponible cuando se muestra el cuadro de diálogo **configurar referencia de servicio** en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="see-also"></a>Vea también
 [Cómo: agregar, actualizar o quitar una referencia de servicio](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [Cómo: agregar una referencia a un servicio Web](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation servicios y WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

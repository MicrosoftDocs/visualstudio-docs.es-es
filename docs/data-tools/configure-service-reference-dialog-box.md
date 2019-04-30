---
title: Configurar referencia de servicio (cuadro de diálogo)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b622fc77884acde5b81d886628afce9f077e86a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567978"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)

El **configurar referencia de servicio** cuadro de diálogo le permite configurar el comportamiento de los servicios de Windows Communication Foundation (WCF).

Para acceder al cuadro de diálogo **Configurar referencia de servicio**, haga clic con el botón derecho en una referencia de servicio en el **Explorador de soluciones** y elija **Configurar referencia de servicio**. También puede acceder al cuadro de diálogo haciendo clic en el botón **Avanzadas** en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="task-list"></a>Lista de tareas

- Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en el campo **Dirección**.

- Para cambiar el nivel de acceso de las clases de un cliente de WCF, seleccione una palabra clave de nivel de acceso en la lista **Nivel de acceso de las clases generadas**.

- Para llamar a los métodos de un servicio WCF asincrónicamente, active la casilla **Generar operaciones asincrónicas**.

- Para generar tipos de contrato de mensaje en un cliente de WCF, active la casilla **Generar siempre contratos de mensaje**.

- Para especificar tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en las listas **Tipo de colección** y **Tipo de colección de diccionario**.

- Para deshabilitar el uso compartido de tipos, desactive la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**. Para habilitar el uso compartido de tipos para un subconjunto de ensamblados a los que se hace referencia, active la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**, seleccione **Volver a usar tipos en los ensamblados especificados** y seleccione las referencias deseadas en la lista **Ensamblados a los que se hace referencia**.

## <a name="uielement-list"></a>Lista de UIElement

 **Dirección**

 Actualiza la dirección web donde se busca una referencia de servicio para un servicio. Por ejemplo, durante el desarrollo, el servicio puede alojarse en un servidor de desarrollo y, a continuación, más adelante moverse a un servidor de producción, se necesitan un cambio de dirección.

> [!NOTE]
> El elemento Dirección no está disponible cuando el cuadro de diálogo **Configurar referencia de servicio** se muestra desde el **cuadro de diálogo Agregar referencia de servicio**.

 **Nivel de acceso para clases generadas**

 Determina el nivel de acceso del código para clases de cliente de WCF.

> [!NOTE]
> En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, vea [Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

 **Generar operaciones asincrónicas**

 Determina si se llama a métodos de servicio WCF sincrónicamente (valor predeterminado) o asincrónica.

 **Generar operaciones basadas en tareas**

 Al escribir código asincrónico, esta opción le permite aprovechar las ventajas de la Task Parallel Library (TPL) que se introdujo con .NET 4. Consulte [biblioteca TPL (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Generar siempre contratos de mensaje**

 Determina si se generan tipos de contrato de mensaje para un cliente WCF. Para obtener más información acerca de los contratos de mensaje, vea [Usar contratos de mensaje](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Tipo de colección**

 Especifica el tipo de colección de lista para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.

 **Tipo de colección de diccionario**

 Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.

 **Volver a usar tipos en ensamblados a los que se hace referencia**

 Determina si un cliente WCF intenta reutilizar lo que ya existe en los ensamblados que se hace referencia en lugar de generar nuevos tipos cuando se agrega o actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.

 **Volver a usar tipos en todos los ensamblados a los que se hace referencia**

 Cuando se selecciona, todos los tipos en el **lista de ensamblados de referencia** se reutilizan si es posible. Esta opción se encuentra activada de forma predeterminada.

 **Volver a usar tipos en los ensamblados especificados**

 Cuando se selecciona, solo los tipos seleccionados en el **lista de ensamblados de referencia** se reutilizan.

 **Ensamblados a los que se hace referencia**

 Contiene una lista de ensamblados de referencia para el proyecto o sitio Web. Al seleccionar **reutilizar tipos en los ensamblados especificados**, puede seleccionar o borrar ensamblados individuales.

 **Agregar referencia web**

 Se abrirá el cuadro de diálogo **Agregar referencia web**.

> [!NOTE]
> Esta opción solo debe usarse para los proyectos que tienen como destino la versión 2.0 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
>
> [!NOTE]
> El **Agregar referencia Web** botón solo está disponible cuando el **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Vea también

- [Cómo: Agregue una referencia a un servicio web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servicios de Windows Communication Foundation y Servicios de datos de WCF](../data-tools/configure-service-reference-dialog-box.md)
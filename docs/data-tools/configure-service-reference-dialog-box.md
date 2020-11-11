---
title: Configurar referencia de servicio (cuadro de diálogo)
description: Use el cuadro de diálogo Configurar referencia de servicio en Visual Studio para configurar el comportamiento de los servicios de Windows Communication Foundation (WCF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1dc1d82b0267e5e0655f3ebef8eb08806ad319a8
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518731"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)

El cuadro de diálogo **configurar referencia de servicio** le permite configurar el comportamiento de los servicios de Windows Communication Foundation (WCF).

Para acceder al cuadro de diálogo **Configurar referencia de servicio** , haga clic con el botón derecho en una referencia de servicio en el **Explorador de soluciones** y elija **Configurar referencia de servicio**. También puede acceder al cuadro de diálogo haciendo clic en el botón **Avanzadas** en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="task-list"></a>Lista de tareas

- Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en el campo **Dirección**.

- Para cambiar el nivel de acceso de las clases de un cliente de WCF, seleccione una palabra clave de nivel de acceso en la lista **Nivel de acceso de las clases generadas**.

- Para llamar a los métodos de un servicio WCF asincrónicamente, active la casilla **Generar operaciones asincrónicas**.

- Para generar tipos de contrato de mensaje en un cliente de WCF, active la casilla **Generar siempre contratos de mensaje**.

- Para especificar tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en las listas **Tipo de colección** y **Tipo de colección de diccionario**.

- Para deshabilitar el uso compartido de tipos, desactive la casilla **Volver a usar tipos en ensamblados a los que se hace referencia**. Para habilitar el uso compartido de tipos para un subconjunto de ensamblados a los que se hace referencia, active la casilla **Volver a usar tipos en ensamblados a los que se hace referencia** , seleccione **Volver a usar tipos en los ensamblados especificados** y seleccione las referencias deseadas en la lista **Ensamblados a los que se hace referencia**.

## <a name="uielement-list"></a>Lista de UIElement

**Dirección**

Actualiza la dirección web en la que una referencia de servicio busca un servicio. Por ejemplo, durante el desarrollo, el servicio se puede hospedar en un servidor de desarrollo y, posteriormente, moverse a un servidor de producción, lo que requiere un cambio de dirección.

> [!NOTE]
> El elemento Dirección no está disponible cuando el cuadro de diálogo **Configurar referencia de servicio** se muestra desde el **cuadro de diálogo Agregar referencia de servicio**.

**Nivel de acceso para clases generadas**

Determina el nivel de acceso del código para clases de cliente de WCF.

> [!NOTE]
> En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, vea [Solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

**Generar operaciones asincrónicas**

Determina si se llama a los métodos de servicio WCF sincrónicamente (el valor predeterminado) o de forma asincrónica.

**Generar operaciones basadas en tareas**

Al escribir código asincrónico, esta opción permite aprovechar las ventajas de la biblioteca TPL (Task Parallel Library) que se presentó con .NET 4. Vea [biblioteca de procesamiento paralelo de tareas (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Generar siempre contratos de mensaje**

Determina si se generan tipos de contrato de mensaje para un cliente de WCF. Para obtener más información acerca de los contratos de mensaje, vea [Usar contratos de mensaje](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Tipo de colección**

Especifica el tipo de colección de lista para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.

**Tipo de colección de diccionario**

Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.

**Volver a usar tipos en ensamblados a los que se hace referencia**

Determina si un cliente de WCF intenta reutilizar lo que ya existe en los ensamblados a los que se hace referencia en lugar de generar nuevos tipos cuando se agrega o actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.

**Volver a usar tipos en todos los ensamblados a los que se hace referencia**

Cuando se selecciona, todos los tipos de la **lista de ensamblados a los que se hace referencia** se reutilizan si es posible. Esta opción está seleccionada de forma predeterminada.

**Volver a usar tipos en los ensamblados especificados**

Cuando se selecciona, solo se reutilizan los tipos seleccionados en la **lista ensamblados a los que se hace referencia** .

**Ensamblados a los que se hace referencia**

Contiene una lista de ensamblados a los que se hace referencia para el proyecto o el sitio Web. Cuando selecciona **volver a usar tipos en ensamblados de referencia especificados** , puede seleccionar o borrar ensamblados individuales.

**Agregar referencia web**

Se abrirá el cuadro de diálogo **Agregar referencia web**.

> [!NOTE]
> Esta opción solo se debe usar para los proyectos que tienen como destino la versión 2,0 del .NET Framework.
>
> [!NOTE]
> El botón **Agregar referencia Web** solo está disponible cuando se muestra el cuadro de diálogo **configurar referencia de servicio** en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="see-also"></a>Consulte también

- [Cómo: Agregar una referencia a un servicio web XML](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servicios de Windows Communication Foundation y WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: abdb65b32f5f660257ecdc4d94fd9fcc387686f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925643"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)

El **configurar referencia de servicio** cuadro de diálogo le permite configurar el comportamiento de los servicios de Windows Communication Foundation (WCF).

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Para tener acceso a la **configurar referencia de servicio** cuadro de diálogo, haga un servicio de referencia en **el Explorador de soluciones** y elija **configurar referencia de servicio**. También puede acceder el cuadro de diálogo, haga clic en el **avanzadas** botón en el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="task-list"></a>Lista de tareas

- Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en la **dirección** campo.

- Para cambiar el nivel de acceso de las clases de un cliente de WCF, seleccione una palabra clave de nivel de acceso en la **acceso a nivel de las clases generadas** lista.

- Para llamar a los métodos de un servicio WCF de forma asincrónica, seleccione la **generar operaciones asincrónicas** casilla de verificación.

- Para generar tipos de contrato de mensaje en un cliente de WCF, seleccione la **generar siempre contratos de mensaje** casilla de verificación.

- Para especificar los tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en el **tipo de colección** y **tipo de colección de diccionario** enumera.

- Para deshabilitar el uso compartido de tipos, desactive el **volver a usar tipos en los ensamblados** casilla de verificación. Para habilitar el uso compartido para un subconjunto de ensamblados de referencia de tipos, seleccione el **volver a usar tipos en los ensamblados** casilla **volver a usar tipos en ensamblados especificados**y seleccione el elemento hace referencia en el **lista de ensamblados de referencia**.

## <a name="uielement-list"></a>Lista de UIElement

 **Dirección**

 Se usa para actualizar la dirección web en la que una referencia de servicio busca un servicio. Por ejemplo, durante el desarrollo un servicio podría hospedarse en un servidor de desarrollo para más adelante moverse a un servidor de producción, lo que hace necesario un cambio de dirección.

> [!NOTE]
> El elemento dirección no está disponible cuando la **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **cuadro de diálogo Agregar referencia de servicio**.

 **Nivel de acceso de las clases generadas**

 Determina el nivel de acceso del código para clases de cliente de WCF.

> [!NOTE]
> En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, consulte [solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

 **Generar operaciones asincrónicas**

 Determina si se llamará a los métodos de servicio de WCF sincrónicamente (valor predeterminado) o asincrónicamente.

 **Generar operaciones basadas en tareas**

 Al escribir código asincrónico, esta opción permite aprovechar las ventajas de la biblioteca TPL, incorporada en .Net 4. Vea [biblioteca TPL (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Generar siempre contratos de mensaje**

 Determina si se generarán tipos de contrato de mensaje para un cliente de WCF. Para obtener más información acerca de los contratos de mensaje, consulte [usar contratos de mensaje](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Tipo de colección**

 Especifica el tipo de colección de lista para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.

 **Tipo de colección de diccionario**

 Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.

 **Volver a usar tipos en ensamblados de referencia**

 Determina si un cliente de WCF intentará volver a usar tipos que ya existen en ensamblados a los que se hace referencia en lugar de generar nuevos tipos cuando se agrega o se actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.

 **Volver a usar tipos en todos los ensamblados que se hace referencia**

 Cuando se selecciona, todos los tipos en el **lista de ensamblados de referencia** se reutilizará si es posible. Esta opción se encuentra activada de forma predeterminada.

 **Volver a usar tipos en ensamblados especificados**

 Cuando se selecciona, sólo los tipos seleccionados en el **lista de ensamblados de referencia** volverá a usar.

 **Lista de ensamblados de referencia**

 Contiene una lista de los ensamblados a los que se hace referencia en el proyecto o sitio web. Cuando **volver a usar tipos en ensamblados especificados** está seleccionada, se pueden activar o borrar ensamblados individuales.

 **Agregar referencia Web**

 Muestra el cuadro de diálogo Agregar referencia Web.

> [!NOTE]
> Esta opción solo debe usarse para proyectos destinados a la versión 2.0 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> El **Agregar referencia Web** botón solo está disponible cuando la **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **cuadro de diálogo Agregar referencia de servicio**.

## <a name="see-also"></a>Vea también

- [Cómo: agregar una referencia a un servicio Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servicios de Windows Communication Foundation y Servicios de datos de WCF](../data-tools/configure-service-reference-dialog-box.md)
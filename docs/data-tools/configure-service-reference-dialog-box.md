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
ms.openlocfilehash: daa18ea2716972daa1429580ad0b2f5be5afe76c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854083"
---
# <a name="configure-service-reference-dialog-box"></a>Configurar referencia de servicio (cuadro de diálogo)

El **configurar referencia de servicio** cuadro de diálogo le permite configurar el comportamiento de los servicios de Windows Communication Foundation (WCF).

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Para tener acceso a la **configurar referencia de servicio** cuadro de diálogo, haga un servicio hace referencia en **el Explorador de soluciones** y elija **configurar referencia de servicio**. También puede acceder haciendo clic en el cuadro de diálogo el **avanzadas** situado en la **Add Service Reference Dialog Box**.

## <a name="task-list"></a>Lista de tareas

- Para cambiar la dirección donde se hospeda un servicio WCF, escriba la nueva dirección en la **dirección** campo.

- Para cambiar el nivel de acceso para las clases en un cliente de WCF, seleccione una palabra clave de nivel de acceso en el **tener acceso a nivel de las clases generadas** lista.

- Para llamar a los métodos de un servicio WCF de forma asincrónica, seleccione el **generar operaciones asincrónicas** casilla de verificación.

- Para generar tipos de contrato de mensaje en un cliente de WCF, seleccione el **generar siempre contratos de mensaje** casilla de verificación.

- Para especificar los tipos de colección de lista o diccionario para un cliente de WCF, seleccione los tipos en el **tipo de colección** y **tipo de colección de diccionario** enumera.

- Para deshabilitar el uso compartido de tipos, desactive la **volver a usar tipos en ensamblados de referencia** casilla de verificación. Para habilitar el uso compartido para un subconjunto de ensamblados de referencia de tipos, seleccione el **volver a usar tipos en ensamblados de referencia** casilla **reutilizar tipos en los ensamblados especificados**y seleccione el elemento hace referencia en el **lista de ensamblados de referencia**.

## <a name="uielement-list"></a>Lista de UIElement

 **Dirección**

 Actualiza la dirección web donde se busca una referencia de servicio para un servicio. Por ejemplo, durante el desarrollo, el servicio puede alojarse en un servidor de desarrollo y, a continuación, más adelante moverse a un servidor de producción, se necesitan un cambio de dirección.

> [!NOTE]
> El elemento dirección no está disponible cuando el **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **Add Service Reference Dialog Box**.

 **Nivel de acceso para clases generadas**

 Determina el nivel de acceso del código para clases de cliente de WCF.

> [!NOTE]
> En los proyectos de sitio web, esta opción siempre está establecida en `Public` y no se puede cambiar. Para obtener más información, consulte [solucionar problemas de referencias de servicio](../data-tools/troubleshooting-service-references.md).

 **Generar operaciones asincrónicas**

 Determina si se llama a métodos de servicio WCF sincrónicamente (valor predeterminado) o asincrónica.

 **Generar operaciones basadas en tareas**

 Al escribir código asincrónico, esta opción le permite aprovechar las ventajas de la Task Parallel Library (TPL) que se introdujo con .NET 4. Consulte [biblioteca TPL (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Generar siempre contratos de mensaje**

 Determina si se generan tipos de contrato de mensaje para un cliente WCF. Para obtener más información acerca de los contratos de mensaje, consulte [mediante contratos de mensaje](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Tipo de colección**

 Especifica el tipo de colección de lista para un cliente de WCF. El tipo predeterminado es <xref:System.Array>.

 **Tipo de colección de diccionario**

 Especifica el tipo de colección de diccionario para un cliente de WCF. El tipo predeterminado es <xref:System.Collections.Generic.Dictionary%602>.

 **Volver a usar tipos en ensamblados de referencia**

 Determina si un cliente WCF intenta reutilizar lo que ya existe en los ensamblados que se hace referencia en lugar de generar nuevos tipos cuando se agrega o actualiza un servicio. Esta opción se encuentra activada de forma predeterminada.

 **Reutilizar tipos en todos los ensamblados que se hace referencia**

 Cuando se selecciona, todos los tipos en el **lista de ensamblados de referencia** se reutilizan si es posible. Esta opción se encuentra activada de forma predeterminada.

 **Reutilizar tipos en los ensamblados especificados**

 Cuando se selecciona, solo los tipos seleccionados en el **lista de ensamblados de referencia** se reutilizan.

 **Lista de ensamblados de referencia**

 Contiene una lista de ensamblados de referencia para el proyecto o sitio Web. Al seleccionar **reutilizar tipos en los ensamblados especificados**, puede seleccionar o borrar ensamblados individuales.

 **Agregar referencia Web**

 Muestra el **Agregar referencia Web** cuadro de diálogo.

> [!NOTE]
> Esta opción solo debe usarse para los proyectos que tienen como destino la versión 2.0 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
> 
> [!NOTE]
> El **Agregar referencia Web** botón solo está disponible cuando el **configurar referencia de servicio** se muestra el cuadro de diálogo desde el **Add Service Reference Dialog Box**.

## <a name="see-also"></a>Vea también

- [Cómo: agregar una referencia a un servicio web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Servicios de Windows Communication Foundation y Servicios de datos de WCF](../data-tools/configure-service-reference-dialog-box.md)
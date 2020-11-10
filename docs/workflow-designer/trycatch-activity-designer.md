---
title: Diseñador de actividades Diseñador de flujo de trabajo-TryCatch
description: Obtenga información sobre la actividad TryCatch y cómo puede usar el diseñador de actividades TryCatch para crear y configurar una actividad TryCatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f1396a60cda1e4e1ad372a73b9c2130d450d746
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433575"
---
# <a name="trycatch-activity-designer"></a>Diseñador de actividades TryCatch

El diseñador de actividades **TryCatch** se usa para crear y configurar una <xref:System.Activities.Statements.TryCatch> actividad.

## <a name="the-trycatch-activity"></a>Actividad TryCatch
 La <xref:System.Activities.Statements.TryCatch> actividad contiene una <xref:System.Activities.Statements.TryCatch.Try%2A> actividad, una colección de **captura \<TException>** y una <xref:System.Activities.Statements.TryCatch.Finally%2A> actividad. Un <xref:System.Activities.Statements.Catch%601> de tipo **TException** contiene un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> y un <xref:System.Activities.Statements.Catch%601.Action%2A> . Todas ellas se utilizan para implementar un mecanismo típico de control de errores basado en excepciones. Una actividad <xref:System.Activities.Statements.TryCatch> intenta ejecutar su actividad <xref:System.Activities.Statements.TryCatch.Try%2A>. Si la <xref:System.Activities.Statements.TryCatch.Try%2A> actividad produce cualquier excepción, la <xref:System.Activities.Statements.TryCatch> actividad utiliza su colección **catch<TException \>** para que coincida con la excepción. Si hay una coincidencia, <xref:System.Activities.Statements.Catch%601.Action%2A> se ejecuta el de la **instrucción Catch \<TException>** correspondiente, que actúa como la lógica de control de errores para la excepción. Si las actividades de la sección <xref:System.Activities.Statements.TryCatch.Try%2A> se completan correctamente o las actividades de <xref:System.Activities.Statements.TryCatch.Catches%2A> se completan correctamente, la actividad <xref:System.Activities.Statements.TryCatch> ejecuta su actividad <xref:System.Activities.Statements.TryCatch.Finally%2A>. Para obtener más información, consulte [excepciones de Windows Workflow](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Utilizar el diseñador de actividades TryCatch

Obtenga acceso al diseñador de actividades **TryCatch** en la categoría **control de errores** del **cuadro de herramientas**.

El diseñador de actividades **TryCatch** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una actividad <xref:System.Activities.Statements.TryCatch> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de TryCatch. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **TryCatch** o en el cuadro **displayName** de la cuadrícula de propiedades. Las demás propiedades se deben editar en la superficie del diseñador de actividades **TryCatch** .

Haga clic en el botón Expandir situado en la esquina superior derecha del diseñador **TryCatch** para ver los cuadros **try** , **catchs** y **Finally** en la vista expandida. Para agregar una captura, haga clic en el botón **Agregar nueva captura** en el diseñador **TryCatch** . El botón cambia a un cuadro combinado de tipo. Seleccione un tipo de excepción y presione ENTRAR para agregar la instrucción catch. Después de agregar una **captura** , el área de captura se expande y se puede colocar una actividad en la captura para definir la lógica de ejecución de la detección. Observe que hay un cuadro de texto a la derecha del área de la instrucción catch expandida. Puede asignar un nombre a la variable de excepción con este cuadro de texto. La variable de excepción solo se puede usar para actividades dentro de la misma **captura**.

El diseñador **TryCatch** no admite la edición de **catch**. Si desea cambiar el tipo de excepción, tiene que eliminar el **bloque** y agregar uno nuevo. Una **instrucción Catch** se puede eliminar seleccionándola y eliminándola, o bien seleccionando **eliminar** en el menú contextual al que se tiene acceso al hacer clic con el botón secundario.

### <a name="the-trycatch-properties"></a>Propiedades TryCatch

En la tabla siguiente se muestran las <xref:System.Activities.Statements.TryCatch> propiedades y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.TryCatch>. El valor predeterminado es TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Falso|La actividad se ejecuta primero cuando <xref:System.Activities.Statements.TryCatch> se ejecuta.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Falso|Colección de elementos **catch** que se va a comprobar cuando la <xref:System.Activities.Statements.TryCatch.Try%2A> actividad produzca una excepción.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Falso|La actividad que se va a ejecutar cuando la clase <xref:System.Activities.Statements.TryCatch.Try%2A> y cualquiera de las actividades necesarias en la colección <xref:System.Activities.Statements.TryCatch.Catches%2A> completen la ejecución.<br /><br /> Necesita agregar al menos una actividad en <xref:System.Activities.Statements.TryCatch.Catches%2A> o en el bloque <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Consulte también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [NotImplementedException](../workflow-designer/throw-activity-designer.md)

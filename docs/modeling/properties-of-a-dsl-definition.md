---
title: Propiedades de las definiciones DSL
description: Obtenga información sobre que las propiedades DslDefinition definen propiedades de definición de lenguaje específicas del dominio, como la numeración de versiones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6212dfcb9e93110a97e7143e5b1c946efebee89f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390846"
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
Las propiedades DslDefinition definen *propiedades de definición de lenguaje específicas* del dominio, como la numeración de versiones. Las propiedades DslDefinition aparecen en la **ventana Propiedades** al hacer clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.

 Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition tiene las propiedades de la tabla siguiente:

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Modificador de acceso|Determina si el modificador de acceso de la clase de dominio es público o interno.|public|
|Atributos personalizados|Atributos definidos personalizados para la clase de dominio.<br /><br /> **Nota** Use el botón Examinar para agregar un atributo.|\<none>|
|Nombre de la empresa|Nombre del nombre actual de la compañía en el registro del sistema.|Nombre actual de la compañía|
|Nombre|Nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres asociado a esta clase de dominio.|Espacio de nombres actual|
|Guid del paquete|GUID para el paquete de Visual Studio generado para este DSL.|\<none>|
|Espacio de nombres del paquete|Espacio de nombres para el paquete de Visual Studio generado para este DSL.|\<none>|
|Nombre de producto|Nombre del producto que se registrará para el paquete de Visual Studio generado para este DSL.|\<none>|
|Notas|Notas asociadas a esta clase de dominio.|\<none>|
|Descripción|Descripción de esta clase de dominio.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave de ayuda asociada a esta clase de dominio.|\<none>|
|Build|Número de compilación incremental para esta definición de lenguaje específico del dominio.|0|
|Major Version|Número de compilación principal incremental para esta definición de lenguaje específico del dominio.|1|
|Minor Version|Número de compilación secundaria incremental para esta definición de lenguaje específico del dominio.|0|
|Revisión|Número de compilación de revisión incremental para esta definición de lenguaje específico del dominio.|0|

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))
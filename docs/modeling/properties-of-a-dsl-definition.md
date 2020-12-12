---
title: Propiedades de las definiciones DSL
description: Obtenga información sobre que las propiedades de DslDefinition definen propiedades de definición de lenguajes específicos del dominio, como la numeración de versiones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48771a61577c5c7ca910cc3b4f8496db37ada281
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360525"
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
Las propiedades de DslDefinition definen propiedades *de definición de lenguajes específicos del dominio* , como la numeración de versiones. Las propiedades DslDefinition aparecen en la ventana **propiedades** cuando se hace clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.

 Para obtener más información, consulte [definición de un lenguaje Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition tiene las propiedades de la tabla siguiente:

|Propiedad.|Descripción|Default|
|-|-|-|
|Modificador de acceso|Determina si el modificador de acceso de la clase de dominio es público o interno.|public|
|Atributos personalizados|Atributos personalizados definidos para la clase de dominio.<br /><br /> **Nota:** Use el botón Examinar para agregar un atributo.|\<none>|
|Nombre de compañía|Nombre del nombre de la compañía actual en el registro del sistema.|Nombre de la empresa actual|
|Nombre|Nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres afiliado a esta clase de dominio.|Espacio de nombres actual|
|GUID del paquete|GUID para el paquete de Visual Studio generado para este DSL.|\<none>|
|Espacio de nombres del paquete|Espacio de nombres para el paquete de Visual Studio generado para este DSL.|\<none>|
|Nombre de producto|Nombre del producto que se registrará para el paquete de Visual Studio generado para este DSL.|\<none>|
|Notas|Notas asociadas a esta clase de dominio.|\<none>|
|Descripción|Descripción de esta clase de dominio.|\<none>|
|Nombre para mostrar|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave de ayuda asociada a esta clase de dominio.|\<none>|
|Build|El número de compilación incremental para esta definición de lenguaje específico de dominio.|0|
|Major Version|El número de compilación principal incremental para esta definición de lenguaje específico de dominio.|1|
|Minor Version|El número de compilación secundaria incremental para esta definición de lenguaje específico de dominio.|0|
|Revisión|El número de compilación de revisión incremental para esta definición de lenguaje específico de dominio.|0|

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))
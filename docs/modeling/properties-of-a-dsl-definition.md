---
title: Propiedades de las definiciones DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cdad251b4440219285ba1341663b7531634ed806
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942248"
---
# <a name="properties-of-a-dsl-definition"></a>Propiedades de las definiciones DSL
Definen propiedades DslDefinition *lenguajes específicos de dominio* propiedades como la numeración de versiones de la definición. Las propiedades DslDefinition aparecen en la **propiedades** ventana al hacer clic en un área abierta del diagrama en el *Diseñador de lenguaje específico de dominio*.

 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition tiene las propiedades en la tabla siguiente:

|Property|Descripción|Default|
|-|-|-|
|Modificador de acceso|Determina si el modificador de acceso de la clase de dominio es público o interno.|public|
|Atributos personalizados|Personalizado definido por los atributos de la clase de dominio.<br /><br /> **Tenga en cuenta** Use el botón Examinar para agregar un atributo.|\<none>|
|Nombre de la compañía|El nombre de la empresa actual en el registro del sistema.|Nombre de la empresa actual|
|nombre|El nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|El espacio de nombres asociado a esta clase de dominio.|Espacio de nombres actual|
|Guid del paquete|El guid del paquete de Visual Studio generado para este DSL.|\<none>|
|Paquete Namespace|El espacio de nombres para el paquete de Visual Studio generado para este DSL.|\<none>|
|Nombre de producto|El nombre del producto que se registrará para el paquete de Visual Studio generado para este DSL.|\<none>|
|Notas|Notas asociadas a esta clase de dominio.|\<none>|
|Descripción|Descripción de esta clase de dominio.|\<none>|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|La palabra clave de ayuda asociada a esta clase de dominio.|\<none>|
|Compilar|El número de compilación incremental para esta definición de lenguaje específico de dominio.|0|
|Versión principal|El número de compilación principal incrementales para esta definición de lenguaje específico de dominio.|1|
|Versión secundaria|El número de compilación secundaria incrementales para esta definición de lenguaje específico de dominio.|0|
|Revisión|La revisión incremental número de compilación para esta definición de lenguaje específico de dominio.|0|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
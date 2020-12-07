---
title: IntelliSense de Visual Basic
description: Obtenga información sobre cómo usar las características de IntelliSense que ofrece el editor de código fuente de Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70cdcf9eb6d741fc579ce555ce0bfa3cdea0d774
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478827"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Archivos de código de IntelliSense para Visual Basic

El editor de código fuente de Visual Basic ofrece las siguientes características de IntelliSense:

## <a name="syntax-tips"></a>Sugerencias de sintaxis

Las sugerencias de sintaxis muestran la sintaxis de la instrucción que está escribiendo. Es útil para instrucciones como [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Finalización automática

- Finalización de varias palabras clave

     Por ejemplo, si escribe `goto` y un espacio, IntelliSense muestra una lista de las etiquetas definidas en un menú desplegable. Otras palabras clave admitidas son `Exit`, `Implements`, `Option` y `Declare`.

- Finalización de `Enum` y `Boolean`

    Si una instrucción va a hacer referencia a un miembro de una enumeración, IntelliSense muestra una lista de los miembros de `Enum`. Si una instrucción va a hacer referencia a un `Boolean`, IntelliSense muestra un menú desplegable con los valores true y false.

La finalización se puede desactivar de forma predeterminada al anular la selección de **Lista de miembros automática** en la página de propiedades **General** de la carpeta **Visual Basic**.

Puede invocar manualmente la finalización al invocar Lista de miembros, Palabra completa o **ALT**+**FLECHA DERECHA**. Para obtener más información, vea [Usar IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense en zona

IntelliSense en zona ayuda a los desarrolladores de Visual Basic que necesitan implementar aplicaciones a través de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y están restringidos a configuraciones de confianza parcial. Esta característica:

- Le permite elegir los permisos con los que se ejecutará la aplicación.

- Muestra las API de la zona elegida como disponibles en Lista de miembros y las API que requieren permisos adicionales como no disponibles.

Para más información, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Listas de finalización filtradas

En Visual Basic, las listas de finalización de IntelliSense tienen dos controles de pestaña situados cerca de la parte inferior de las listas. En la pestaña **Común**, que está seleccionada de forma predeterminada, se muestran los elementos que se usan con más frecuencia para completar la instrucción que se está escribiendo. En la pestaña **Todos** se muestran todos los elementos que están disponibles para la finalización automática, incluidos aquellos que también están en la pestaña **Común**.

## <a name="see-also"></a>Consulte también

- [Uso de IntelliSense](../ide/using-intellisense.md)

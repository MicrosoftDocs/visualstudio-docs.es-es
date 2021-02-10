---
title: Caracteres especiales de escape | Microsoft Docs
description: Obtenga información sobre los caracteres especiales que se deben escapar únicamente si tienen un significado especial en el contexto en que se utilicen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e665c214ea75de67a6c339bb516dfb812936448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878154"
---
# <a name="special-characters-to-escape"></a>Caracteres especiales de escape

Los caracteres especiales deben ser de escape únicamente si tienen un significado especial en el contexto en que se utilicen. Por ejemplo, el asterisco (*) es un carácter especial solo en los atributos "Include" y "Exclude" de una definición de elemento, o en una llamada a <xref:Microsoft.Build.Tasks.CreateItem>. En los demás casos, el asterisco se trata como un asterisco literal. Aunque no es necesario que los asteriscos sean de escape en todos los archivos del proyecto, tampoco es perjudicial.

 Utilice la notación %\<xx> en lugar del carácter especial, donde \<xx> representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (*) como un carácter literal, utilice el valor `%2A`.

 A continuación se enumera la lista completa de los caracteres especiales de escape:

|Carácter|Codificación ASCII|Descripción|
|---------|----------|-----------|
|%|%25|Signo de porcentaje, utilizado para hacer referencia a metadatos.|
|$|%24|Signo de dólar, utilizado para hacer referencia a propiedades.|
|@|%40|Arroba, utilizada para hacer referencia a listas de elementos.|
|(|% 28|Paréntesis de apertura, utilizado en listas.|
|)|% 29|Paréntesis de cierre, utilizado en listas.|
|;|%3B|Punto y coma, utilizado como separador de lista.|
|?|%3F|Signo de interrogación, utilizado como carácter comodín para describir una especificación de archivo en la sección Include/Exclude de un elemento.|
|* |%2A|Asterisco, utilizado como carácter comodín para describir una especificación de archivo en la sección Include/Exclude de un elemento.|

> [!NOTE]
> En algunos escenarios, puede que tenga que escapar caracteres de comillas dobles ("), como cuando se usan dentro de una tarea `Exec`.

## <a name="see-also"></a>Vea también

- [Cómo: Usar caracteres de escape especiales en MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)

---
title: Caracteres especiales de escape | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632256"
---
# <a name="special-characters-to-escape"></a>Caracteres especiales de escape

Los caracteres especiales deben ser de escape únicamente si tienen un significado especial en el contexto en que se utilicen. Por ejemplo, el asterisco (*) es un carácter especial solo en los atributos "Include" y "Exclude" de una definición de elemento, o en una llamada a <xref:Microsoft.Build.Tasks.CreateItem>. En los demás casos, el asterisco se trata como un asterisco literal. Aunque no es necesario que los asteriscos sean de escape en todos los archivos del proyecto, tampoco es perjudicial.

 Utilice la notación %\<xx> en lugar del carácter especial, donde \<xx> representa el valor hexadecimal del carácter ASCII. Por ejemplo, para usar un asterisco (*) como un carácter literal, utilice el valor `%2A`.

 A continuación se enumera la lista completa de los caracteres especiales de escape:

|Carácter|Descripción|
|---------------|-----------------|
|%|Signo de porcentaje, utilizado para hacer referencia a metadatos.|
|$|Signo de dólar, utilizado para hacer referencia a propiedades.|
|@|Arroba, utilizada para hacer referencia a listas de elementos.|
|(|Paréntesis de apertura, utilizado en listas.|
|)|Paréntesis de cierre, utilizado en listas.|
|;|Punto y coma, utilizado como separador de lista.|
|?|Signo de interrogación, utilizado como carácter comodín para describir una especificación de archivo en la sección Include/Exclude de un elemento.|
|*|Asterisco, utilizado como carácter comodín para describir una especificación de archivo en la sección Include/Exclude de un elemento.|

> [!NOTE]
> En algunos escenarios, puede que tenga que escapar caracteres de comillas dobles ("), como cuando se usan dentro de una tarea `Exec`.

## <a name="see-also"></a>Vea también

- [Cómo: Usar caracteres de escape especiales en MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)

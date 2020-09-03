---
title: 'Error: no se puede copiar el&#39; de archivos de dependencia &#39;en el proyecto de Project&#39; &#39;en el directorio de ejecución porque entraría en conflicto con el archivo de &#39;de dependencia&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656050"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Error: no se puede copiar el archivo de &#39;de dependencia&#39; en Project &#39;Project&#39; en el directorio de ejecución porque entraría en conflicto con el archivo de &#39;de dependencia&#39;
Existe un conflicto entre referencias; se está copiando más de una dependencia distinta con el mismo nombre de archivo en el directorio bin para que la aplicación se ejecute. El directorio de ejecución no puede resolver el conflicto porque ninguna de las dependencias es una referencia principal.

 Este error impedirá que la compilación se lleve a cabo.

 Haga doble clic en este elemento de lista de tareas para ir al nodo de referencias del proyecto en el que se ha producido el conflicto.

 **Para corregir este error**

- Convierta uno de los ensamblados en una referencia directa del proyecto. Un posible inconveniente de este método es que no está garantizado que el ensamblado que elija funcione con los ensamblados que pueden requerir alguna otra versión del ensamblado al que se hace referencia.

     \- o -

- Procure que ambas copias del ensamblado tengan nombres seguros y estén en la memoria caché global de ensamblados. Así, no será necesario copiar los ensamblados en el directorio bin.

## <a name="see-also"></a>Consulte también
 [Administrar referencias en una](../ide/managing-references-in-a-project.md) [caché global de ensamblados](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) de un proyecto [ensamblados con nombre seguro](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [control de versiones de ensamblado](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Cómo: crear y quitar dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)
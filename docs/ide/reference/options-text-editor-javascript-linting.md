---
title: Opciones, Editor de texto, JavaScript, detección de errores
description: Aprenda a usar la página Detección de errores del cuadro de diálogo Opciones para establecer las opciones para analizar código en el Editor de código.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0458495920b603ebbfc2befb733bd8618cea5310
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932350"
---
# <a name="options-dialog-box-text-editor--javascripttypescript--linting"></a>Cuadro de diálogo Opciones: Editor de texto \> JavaScript/TypeScript \> Linting

Use la página **Detección de errores** del cuadro de diálogo **Opciones** para establecer las opciones para analizar el código en el Editor de código. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y, luego, expanda **Editor de texto** > **JavaScript/TypeScript** > **Linting**.

## <a name="eslint-settings"></a>Configuración de ESLint

Estas opciones le permiten habilitar el análisis de código estático de JavaScript y TypeScript y elegir los archivos que se van a analizar. Para información sobre ESLint, consulte [ESLint.org](https://eslint.org/).

### <a name="uielement-list"></a>Lista de UIElement

|Opción|Descripción|
|------------|-----------------|
|**Habilitar ESLint**|Cuando se selecciona esta opción, el Editor de código permite realizar un análisis estático del código.|
|**Detectar errores de estilo en todos los archivos del proyecto, incluidos los archivos cerrados**|Cuando se selecciona esta opción, se analizan los archivos cerrados, a menos que solo se informen los diagnósticos de archivos abiertos.|

## <a name="global-eslint-config-options"></a>Opciones de configuración global de ESLint

Esta opción le permite copiar la ubicación del archivo de configuración global de ESLint. Además, si anteriormente se cambió la ubicación, puede restablecer el archivo a la ubicación predeterminada.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
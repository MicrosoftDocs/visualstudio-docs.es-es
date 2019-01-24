---
title: Opciones, Editor de texto, JavaScript, detección de errores
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfef5db28b187d88c49cb6c35a0e008e78198cc4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350307"
---
# <a name="options-text-editor-javascript-linting"></a>Opciones, Editor de texto, JavaScript, detección de errores

Use la página **Detección de errores** del cuadro de diálogo **Opciones** para establecer las opciones para analizar el código en el Editor de código. Para acceder a esta página, en la barra de menús elija **Herramientas** > **Opciones** y expanda **Editor de texto** > **JavaScript** > **Detección de errores**.

## <a name="eslint-settings"></a>Configuración de ESLint

Estas opciones le permiten habilitar el análisis de código estático de JavaScript y elegir los archivos que se van a analizar. Para información sobre ESLint, consulte [ESLint.org](https://eslint.org/).

### <a name="uielement-list"></a>Lista de UIElement

|Opción|Descripción|
|------------|-----------------|
|**Habilitar ESLint**|Cuando se selecciona esta opción, el Editor de código permite realizar un análisis estático del código.|
|**Detectar errores de estilo en todos los archivos del proyecto, incluidos los archivos cerrados**|Cuando se selecciona esta opción, se analizan los archivos cerrados, a menos que solo se informen los diagnósticos de archivos abiertos.|

## <a name="global-eslint-config-options"></a>Opciones de configuración global de ESLint

Esta opción le permite copiar la ubicación del archivo de configuración global de ESLint. Además, si anteriormente se cambió la ubicación, puede restablecer el archivo a la ubicación predeterminada.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
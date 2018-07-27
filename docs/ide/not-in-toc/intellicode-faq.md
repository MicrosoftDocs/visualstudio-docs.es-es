---
title: Preguntas y respuestas sobre IntelliCode
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079316"
---
# Preguntas más frecuentes de Visual Studio IntelliCode

Gracias por su interés en Visual Studio IntelliCode. Se espera que estas breves preguntas más frecuentes respondan a algunas de las preguntas que pueda tener.

## P. ¿Qué es Visual Studio IntelliCode?

En la compilación 2018, Microsoft presentó Visual Studio IntelliCode, una nueva funcionalidad que mejora el desarrollo de software mediante IA. IntelliCode ayuda a los desarrolladores y a los equipos a programar con confianza, encontrar problemas con mayor rapidez y centrarse en las revisiones del código.

Una primera vista de IntelliCode demostró cómo mejora el proceso de desarrollo de software de las maneras siguientes:

- Ofrece finalizaciones de código en contexto
- Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo
- Encuentra problemas de código difíciles de detectar
- Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan

Los desarrolladores pueden buscar más información y registrarse para recibir noticias y obtener versiones preliminares privadas futuras en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Qué permite hacer Visual Studio IntelliCode a los clientes?

Visual Studio IntelliCode es una gama de capacidades que ofrece nuevas mejoras de productividad a través de la inteligencia artificial (IA).

Los desarrolladores pueden [descargar una extensión experimental](https://go.microsoft.com/fwlink/?linkid=872707) para Visual Studio 2017, versión 15.7 y posteriores. La extensión proporciona en este momento:

- IntelliSense mejorado con IA que predice la API correcta más posible para uso por parte del desarrollador, en lugar de simplemente presentar una lista alfabética de miembros. Usa el contexto de código actual y patrones del desarrollador para proporcionar esta lista dinámica.

- Inferencia de estilo de código y convenciones de formato que ayuda a mantener el código coherente al crear dinámicamente un [archivo .editorconfig](../create-portable-custom-editor-options.md) a partir del código base para estilos y formatos de codificación. Estas convenciones permiten que Visual Studio ofrezca correcciones de estilo y formato automáticas para limpiar el documento.

Actualizaremos la extensión con más funcionalidades en los próximos meses.

## P. ¿Por qué la inferencia de EditorConfig antepone un 1 al nombre de archivo?

Un problema conocido de la extensibilidad de Visual Studio hace que se anteponga un 1 al nombre de archivo .editorconfig cuando se crea al hacer clic con el botón derecho y elegir **Agregar > Nuevo elemento**. El procesador de editorconfig de Visual Studio no reconoce los archivos nombrados de esta manera. Este problema se corrige en Visual Studio 2017 versión 15.8 Preview 4, pero hasta entonces puede solucionarlo si quita el 1 en el cuadro de diálogo **Agregar nuevo elemento**.

## P. No veo que se apliquen las convenciones de EditorConfig. ¿Por qué?
Hay un par de motivos comunes por los que puede producirse este problema:

- En las versiones de Visual Studio 2017 anteriores a 15.8 Preview 3, debe cerrar y volver a abrir todos los documentos abiertos para ver las convenciones del archivo EditorConfig creado aplicadas. Este problema se ha corregido en la versión 15.8 Preview 3.
- Las convenciones de formato nunca se muestran en la **lista de errores** ni como "subrayados ondulados" en el código. Pero pueden corregirse con la nueva extensión Dar formato al documento (Ctrl+K, Ctrl+D) de Visual Studio 2017 versión 15.8 Preview 3 o posterior

## P. Dar formato al documento no corrige las convenciones de estilo. ¿Por qué?
Hay un par de motivos comunes por los que puede producirse este problema:

- Quizás no esté usando Visual Studio 2017 versión 15.8 Preview 3 o superior. Necesita esta versión para poder usar el comando "Dar formato al documento" extendido para realizar una limpieza de código adicional para el documento actual.
- Quizás no haya elegido las correcciones de estilo. La capacidad extendida de corrección de problemas basados en convenciones de Dar formato al documento solo cubre un conjunto fijo de problemas. Puede cambiar los problemas que se corrigen en **Herramientas-Opciones**, en **Editor de texto > C# > Estilo de código > Formato > General > Configuración para dar formato al documento (experimento)**. Observe que la configuración predeterminada no corrige algunas convenciones de estilo. Puede elegirlas en **Herramientas > Opciones**. Por ejemplo "Aplicar preferencias de tipos implícitos o explícitos" ejecuta reglas de estilo sobre el uso de `var`.

## P. ¿Qué convenciones de EditorConfig puede deducir Visual Studio IntelliCode?

En este momento, esta característica es experimental, por lo que aún no se admite el conjunto completo de convenciones documentadas en la [referencia de configuración de estilos de código](../editorconfig-code-style-settings-reference.md).

IntelliCode actualmente puede deducir las convenciones siguientes:

Convenciones de formato:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Convenciones de estilo
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## P. ¿Hay otras características que se vayan a incorporar a la extensión IntelliCode de Visual Studio?

Estamos trabajando de forma activa en una serie de funcionalidades que estamos ansiosos por compartir públicamente cuando estén disponibles. Puede registrarse para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode) y ser el primero en enterarse cuando tengamos nuevas funciones disponibles.

## P: ¿Qué hace que "IntelliSense asistido por IA", con la tecnología de IntelliCode, sea mejor que el IntelliSense corriente?

Con IntelliCode, la lista de finalización sugiere la API que es probablemente más correcta para que use un desarrollador, en lugar de presentar una simple lista alfabética de los miembros. Usa el contexto de código actual del desarrollador y patrones basados en 2000 proyectos de código abierto de alta calidad en GitHub, cada uno con más de 100 estrellas, para proporcionar esta lista dinámica. Los resultados forman un modelo que predice las llamadas API más probables y más relevantes.

## P: ¿Cuál es la calidad de las sugerencias de finalización de IntelliCode?

Hemos estado usando las recomendaciones de IntelliCode de forma interna en Microsoft durante algún tiempo y creemos que las sugerencias son útiles. Aunque, en última instancia, será usted quien tenga que probar lo útiles que son estas recomendaciones mientras escribe código. Nos encantaría que le diera una oportunidad a la [extensión Visual Studio IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707). Háganos saber si le sirve y envíenos sus comentarios. También entrenaremos nuestro modelo en función de lo que elija en nuestras recomendaciones y actualizaremos la extensión según mejore el modelo.

> [!NOTE]
> No se recopila ningún código definido por el usuario. Consulte la pregunta sobre [privacidad](#privacy).

## P. ¿Cuál es el futuro de IntelliCode?

Estamos estudiando una amplia variedad de formas de mejorar la productividad del desarrollador mediante IA y otras técnicas avanzadas. En Microsoft Build 2018 mostramos una primera vista de algunos de los escenarios donde creemos que la IA podría ayudar a los desarrolladores, pero hay muchas más. Estamos interesados en obtener información de los desarrolladores que experimenten con lo que hemos mostrado, así que regístrese para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Cuánto cuesta?

Actualmente no disponemos de ningún anuncio sobre los precios.

## P. ¿Cuándo se lanzará IntelliCode?

IntelliSense asistido por IA de IntelliCode actualmente se encuentra en su primera versión preliminar experimental. Seguiremos actualizando la extensión experimental y agregaremos más capacidades en el futuro. No tenemos ninguna programación sobre la versión final, pero agradecemos los comentarios de los desarrolladores, para que podamos proporcionar las mejores experiencias posibles. Puede registrarse para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Esta experiencia solo está disponible en Visual Studio y para C#?

La experiencia se mostró en la compilación 2018 en Visual Studio 2017, en un código de base de C#. Pero esperamos expandir IntelliCode a más idiomas y herramientas de la familia de Visual Studio en el futuro.

## P. <a name="whynointellisense"/> No veo las sugerencias de IntelliCode en mi experiencia de edición de C#. ¿Qué sucede?

Las sugerencias de IntelliCode aparecen en la interfaz de usuario estándar de IntelliSense de Visual Studio para C#. Las extensiones que reemplazan esa interfaz de usuario evitan que las sugerencias con estrella de IntelliCode aparezcan en la parte superior de la lista. Para comprobar si las extensiones están causando este comportamiento, desactívelas y vuelva a probar IntelliSense.

Si con esto no se resuelve el problema, notifíquelo mediante la característica [Notificar un problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) de Visual Studio y mencione a IntelliCode en el informe.

## P. ¿Qué versión de Visual Studio necesito para ejecutar esta extensión?

La extensión Visual Studio IntelliCode es compatible con Visual Studio 2017 versión 15.7 (versión preliminar 5) y posteriores (todas las SKU). La instalación de la extensión se detiene con el mensaje “Esta extensión no se puede instalar en ninguno de los productos instalados actualmente” si no tiene instalada la versión mínima requerida.

## P. ¿Esta experiencia solo está disponible en inglés?

IntelliCode es actualmente una extensión de versión preliminar y estamos entusiasmados por comprender lo útiles que resultan estas capacidades a un conjunto amplio de clientes. Cuando saquemos IntelliCode de la versión preliminar, por supuesto que tendremos en cuenta qué configuración regional o idioma admitiremos primero y cómo se empaquetará, en función de sus comentarios.

## <a name="privacy"/> P: ¿Qué hay de la privacidad? ¿Se enviará mi código a la nube? ¿Qué datos de clientes se envían a Microsoft?

Invitamos a los desarrolladores a probar Visual Studio IntelliCode hoy como una extensión de versión preliminar experimental. El propósito de la extensión es permitir a los desarrolladores que prueben las capacidades de IntelliCode y proporcionen comentarios al equipo del producto.

Se capturan algunos datos de uso de informe de errores anónimos de la extensión para ayudar a mejorar el producto. No se envía ningún código definido por el usuario a Microsoft, pero recopilamos información sobre el uso de los resultados de IntelliCode. Los datos solo incluyen tipos de .NET y de código abierto, y los miembros que ha seleccionado de la lista de sugerencias de IntelliCode. Los desarrolladores pueden optar por no participar en el [Programa para la mejora de la experiencia de Visual Studio](../../ide/visual-studio-experience-improvement-program.md), que también desactiva la recopilación de datos para la extensión IntelliCode. En la barra de menús, seleccione **Ayuda** > **Enviar comentarios** > **Configuración**. En el cuadro de diálogo **Programa de mejora de experiencia de Visual Studio**, seleccione **No, prefiero no participar** y, después, seleccione **Aceptar**.

La extensión de IntelliCode podría preguntar al desarrollador periódicamente para que complete una encuesta, que también es anónima. Los usuarios podrán registrarse para recibir noticias y obtener una vista previa privada futura, pero no es necesario que lo hagan actualmente para usar la extensión experimental.

Las características futuras podrían requerir acceso a un servicio, lo que requerirá que se registren. Publicaremos información más detallada cuando dichas características estén listas para la versión preliminar privada.

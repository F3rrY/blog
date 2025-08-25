---
title: Así creé mi blog gratis y rápido
parent: Notas
nav_order: 1
tags: [blog, crear blog gratis, blog gratis]
---

## Así creé mi blog gratis y rápido

Cuando el otro día avisé de forma oficial sobre la creación de mi blog en mis redes, anuncié que iba a publicar un artículo sobre cómo lo había creado, ya que creo que puede llegar a ser interesante para más de uno.

Quiero comenzar diciendo que he dejado de lado la forma "natural" de tener un blog (contratar un hosting, instalar WordPress, etc.), sino que esta vez he utilizado una solución óptima. En pleno 2025 no quería pagar por un hosting y estar al tanto del mantenimiento, controlar los agujeros de seguridad, actualizar versiones de WordPress y tener en cuenta cosas superfluas... La verdad es que todo esto ya me da bastante pereza a estas alturas. Así que he tirado por otra vía: montar una página estática (Static Page). Y, la verdad, esta solución y visto el resultado, ha sobrepasado todas mis expectativas.

Sabía del potencial que ofrecen las páginas estáticas debido a que, dada su naturaleza de no realizar ningún tipo de petición al servidor, **hace que sean muy rápidas** y apenas tengan latencia/retraso al cargar las páginas, que básicamente es lo que busca el usuario cuando entra a una web, que sea lo más rápida posible. Pero, sinceramente, no me esperaba que lo fueran tanto.

## Requisitos técnicos

{: .highlight }
Para llegar a este punto hay que tener ciertos conocimientos de programación o conocimientos básicos de GitHub/Cloudflare.

- **Hosting**: Me decidí por alojar el blog en **GitHub** mediante **GitHub Pages**, debido a que con el plan gratuito tienes más que de sobra y además es muy fácil de configurar. Además, al estar integrado con GitHub, me permite tener un control de versiones de todo el contenido del blog. Además, tengo los DNS que apuntan a **Cloudflare**, ya que me permite tener un mejor control de las DNS, caché de los recursos, protección de ataques DDoS, etc. Y, lo mejor de todo, es que con el plan gratuito te alcanza.
- **Dominio**: El dominio es lo único en lo que he tenido que invertir, ya que las opciones que me ofrecían servicios gratuitos como Freenom no me convencían.
- **Plantilla**: Para la plantilla del blog, he utilizado Jekyll, que es un generador de páginas estáticas muy popular y bastante fácil de usar. Jekyll me permite crear páginas HTML a partir de archivos ***Markdown***.
- **Editor de texto**: Para escribir los artículos, utilizo **Visual Studio Code**, que es un editor de código muy potente y versátil. Además, los plugins que tiene me facilitan la escritura en Markdown (veo los cambios al momento) y desplegar los cambios al repositorio de GitHub.
- **Analytics**: Para las estadísticas utilizo **Google Analytics**, y a pesar de que Cloudflare ya tiene su propio sistema de analytics, la verdad que no me ofrece cosas tan básicas que necesito como saber las páginas más vistas, etc. Se centra en métricas muy básicas y sencillas, y yo busco profundizar más, cosa que Google Analytics sí que me ofrece.

## ¿Cómo funciona?

La verdad es que es muy sencillo, más de lo que pensáis después de todo el tinglado que hay montado. Abro Visual Studio Code, creo un nuevo archivo Markdown (cuya extensión es .md), escribo el artículo en texto plano con las distintas etiquetas de Markdown para las negritas, cursivas, listas, enlaces, etc. Lo reviso en local (con Bundle ejecutando Jekyll en modo servidor) y, si está todo OK, hago el commit/push a GitHub.

Y GitHub, cuando detecta los cambios en el repositorio, dispara el proceso de generación de la página estática y, al cabo de unos segundos, los cambios ya están disponibles. Y todo con la máxima velocidad/optimización y seguridad posible que ofrece una página estática.

## ¿Funciona también con WordPress?

¿Podía haber usado WordPress? Sí, por supuesto, pero no quería complicarme la vida. Conozco WordPress desde 2009, cuando creé mi primer blog ([Universobit][UniversobitUrl]), que fue el germen de lo que llegaría a ser más adelante [Compunoticias][CompunoticiasUrl]. Pero sí que es cierto que, con el paso de los años, WordPress ha ido creciendo tanto en potencia como en complejidad: el famoso editor Gutenberg, el maquetador Elementor, etc. Como comento, todo eso eleva la complejidad, distrayendo de lo que realmente importa, que es la **publicación de contenido**. Yo quería algo más simple y sencillo: Abrir el editor, escribir y publicar, punto. De hecho, ya veis que el diseño es minimalista y simple: La página no tiene plugins, no tiene slider, no tiene colores chillones ni nada que te distraiga de la lectura.

Y volviendo a la pregunta, ¿se puede montar una Static Pages con WordPress? Y la respuesta es **sí**, con WordPress también puedes montar una Static Page. Y, de hecho, [Marc Pampols][MarcPampolsUrl] aquí lo explica realmente bien.

## Google PageSpeed

Para los que no lo conozcáis, **Google PageSpeed** es una herramienta de Google que mide la velocidad de carga de una página web, viendo dónde se producen cuellos de botella y por qué tu web carga lento. Pues bien, el tener una página estática y con todos los recursos en local sin tener que hacer peticiones a un servidor externo hace que la puntuación **se dispare**. No es automático, pero ya la primera vez que lo pasé, ya me dio una puntuación de alrededor de un 90/100. Para llegar a la perfección, hay que hacer algún que otro ajuste que requiere que sepas lo que tocas. Pero, una vez modificado, pues 100/100.

![image info](/assets/images/pagespeed.avif)

[MarcPampolsUrl]: https://www.marcpampols.net/es/100-de-pagespeed-y-0e-de-hosting/
[UniversobitUrl]: https://web.archive.org/web/20100131062034/http://www.universobit.net/?p=1548
[CompunoticiasUrl]: https://web.archive.org/web/20110217101527/http://compunoticias.com/
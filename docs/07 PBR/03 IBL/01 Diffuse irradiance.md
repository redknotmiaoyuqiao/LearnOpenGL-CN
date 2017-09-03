# 漫反射辐照

原文     | [Diffuse irradiance](https://learnopengl.com/#!PBR/IBL/Diffuse-irradiance)
      ---|---
作者     | JoeyDeVries
翻译     | [Redknot](https://github.com/redknotmiaoyuqiao)
校对     | 暂无

!!! Important

	注意： 作者正在对PBR章节进行大的调整，原文的内容时时可能有更新，建议仍是阅读原文。

!!! Important

IBL or image based lighting is a collection of techniques to light objects, not by direct analytical lights as in the previous tutorial, but by treating the surrounding environment as one big light source. This is generally accomplished by manipulating a cubemap environment map (taken from the real world or generated from a 3D scene) such that we can directly use it in our lighting equations: treating each cubemap pixel as a light emitter. This way we can effectively capture an environment's global lighting and general feel, giving objects a better sense of belonging in their environment.

IBL <def>基于图像的光照技术</def>(image based lighting) 是一种使用collection来照亮物体的技术，和从前课程中直接分析光照是不一样的，但是我们仍然可以将环绕周围的环境看作是一个大的光源。

As image based lighting algorithms capture the lighting of some (global) environment its input is considered a more precise form of ambient lighting, even a crude approximation of global illumination. This makes IBL interesting for PBR as objects look significantly more physically accurate when we take the environment's lighting into account.

To start introducing IBL into our PBR system let's again take a quick look at the reflectance equation:

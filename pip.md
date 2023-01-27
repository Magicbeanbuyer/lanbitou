pip can install from either [[Source Distribution]]s (sdist) or [[Wheel]]s, but if both are present on PyPI, pip will prefer a compatible wheel. You can override pip`s default behavior by e.g. using its –no-binary option.

Wheels are a pre-built distribution format that provides faster installation compared to Source Distributions (sdist), especially when a project contains compiled extensions.

If pip does not find a wheel to install, it will locally build a wheel and cache it for future installs, instead of rebuilding the source distribution in the future.



build
```
${SRCROOT}/fastlane/SwiftGen/bin/swiftgen 
xcassets --param enumName=${TARGETNAME}Asset 
 --param imageTypeName=${TARGETNAME}ImageAsset
 --param colorTypeName=${TARGETNAME}ColorAsset 
 --param colorAliasName=${TARGETNAME}Color 
 --param imageAliasName=${TARGETNAME}Image -p 
 
 ${SRCROOT}/fastlane/SwiftGen/____xxxxxxxxXXXXXXXX____ActiveTemplates/xcassets.stencil 
 ${SRCROOT}/${TARGETNAME}/Resources/Assets.xcassets -o 
${SRCROOT}/${TARGETNAME}/SwiftGen/SwiftGenXcassets.swift

```

strings.stencil
```stencil
{% if tables.count > 0 %}
import Foundation

// swiftlint:disable file_length
{% macro parametersBlock types %}{% filter removeNewlines:"leading" %}
  {% for type in types %}
    _ p{{forloop.counter}}: {{type}}{% if not forloop.last %}, {% endif %}
  {% endfor %}
{% endfilter %}{% endmacro %}
{% macro argumentsBlock types %}{% filter removeNewlines:"leading" %}
  {% for type in types %}
    p{{forloop.counter}}{% if not forloop.last %}, {% endif %}
  {% endfor %}
```

swiftgen_strings.sh

```rb
${SRCROOT}/fastlane/SwiftGen/bin/swiftgen strings --param enumName=NSDStrings 
"${SRCROOT}/${TARGETNAME}/Resources/Base.lproj/NSD.strings" -p ${SRCROOT}
/fastlane/SwiftGen/VitalityActiveTemplates/strings.stencil -o "${SRCROOT}/${TARGETNAME}/Resources/NSD.strings.swift"
```

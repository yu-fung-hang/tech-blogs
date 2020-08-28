# @NotNull vs @NotEmpty vs @NotBlank

## Comparison

* `@NotNull` : a constrained CharSequence, Collection, Map, or Array is valid as long as it's not null, but it can be empty;
* `@NotEmpty` : a constrained CharSequence, Collection, Map, or Array is valid as long as it's not null and its size/length is greater than zero;
* `@NotBlank` : a constrained String is valid as long as it's not null and the trimmed length is greater than zero.

## Reference
* https://www.baeldung.com/java-bean-validation-not-null-empty-blank
# pattern_library

The purpose of the library was to distill the designs of the websites into reusable chunks of CSS that can be added to a website with their corresponding HTML to provide the bulk of the heavy lifting when it comes to providing a responsive website with common patterns used on the websites. My aim is that the code is as modular as possible to decrease unintended side effects of adding classes to elements haphazardly. It was also important that these components could be modified to fit a website’s theme or adjust to varies constraints. 

I drew a lot of inspiration from two particular articles, [Architecting Front End Styles](https://thoughtbot.com/blog/architecting-front-end-styles) and [MindBEMding: Getting Your Head Around BEM Syntax](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/). 

## Library Setup:

The base folder will hold the set of core elements (HTML), any SCSS mixins, functions, placeholders, etc. and the typography settings. Components would be the next step higher in complexity. This will hold individual elements that make up the components on the sidebar, the archive selector or a media element such as audioplayer.scss. Patterns are when multiple components start to fit together, such as the article rating, the comment section, the header, etc..

BEM is a naming methodology thought up at Yandex. It is a way of naming your CSS classes to give them more transparency and meaning to other developers.

The Naming convention follows this pattern:

    .block {}
    .block__element {}
    .block--modifier {}

.block represents the higher level of an abstraction or component.

.block__element represents a descendant of .block that helps form .block as a whole.

.block--modifier represents a different state or version of .block.

BEM syntax for the same HTML form.

    <form class="search-form  search-form--full">
      <input type="text" class="search-form__input">
      <input type="Submit" value ="Search" class="search-form__button">
    </form>

The CSS for the above markup would be as follows:

    .search-form {} /* Block /
    .search-form__input {} / Element /
    .search-form--full {} / Modifier */

This would help prevent unknown side effects and limit bad practices for adding classes like .button to a search form and also a comment form. BEM provides a way to write more modular CSS that avoids inheritance pitfalls and provides the potential for scope when using unique classes such as search-form__input.

SCSS nesting allows for an easy way to write CSS with the BEM convention. The following code will create:

    .most-popular {
      &__title {
        padding: 0.5rem;
        margin: 0;
        background-color: #4d5158;
        color: $white;
        font-size: 1rem;
        font-weight: normal;
      }
      &__item {
        display: block;
        padding: 0.5rem 1rem;
        background-color: #35383d;
        color: $white;
        @extend %text-decoration-none;
        @extend %hover-underline;
      }
    }

## Guidance
Answer the following questions considering the learning outcomes for
- [Week 010](https://learn.foundersandcoders.com/course/syllabus/developer/week10-project05-DOTNET-intro/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Evidence of Learning Outcomes Achieved

- This week, I familiaried with the primary directories and core files in WordPress (`wp-content`, `wp-includes`, `wp-admin`, `index.php`, `wp-config.php`, `.htaccess`) to understand their roles and purposes within a WordPress site. 


- I configured a local environment with MAMP, Apache, and phpMyAdmin, establishing a WordPress database connection through wp-config.php.

    ```php
    // wp-config.php configuration
    define('DB_NAME', 'wordpress_db');
    define('DB_USER', 'root');
    define('DB_PASSWORD', 'password');
    define('DB_HOST', 'localhost');
    ```


- Using `theme.json` I controlled global theme settings and styles by configuring a colour palette, typography, and button styles, which helped manage styles centrally.

    ```json
    {
      "version": 3,
      "settings": {
        "color": {
          "palette": [
            { "color": "#ffffff", "name": "Base", "slug": "base" },
            { "color": "#000000", "name": "Contrast", "slug": "contrast" },
            { "color": "#89cff0", "name": "Primary", "slug": "primary" }
          ]
        }
      }
    }
    ```


- I implemented reusable template parts, such as `header.html` and `footer.html`, helping me understand the modularity of WordPress block themes.

    ```html
    <!-- wp:template-part {"slug":"header","area":"header","tagName":"header"} /-->
    ```

- I registered a custom hero block pattern using PHP, enabling a dynamic hero section that includes a heading, subheading, and buttons. The block pattern is defined in `hero.php`, which adds flexibility by allowing users to insert this section wherever needed.

```
<!-- wp:cover {"url":"<?php echo esc_url(get_theme_file_uri('assets/images/hero-background.jpg')); ?>","dimRatio":50,"overlayColor":"contrast","align":"full"} -->
```

- Initially, I tried building a theme using PHP templates, realising later that block themes rely on HTML templates and theme.json configurations.
```
<?php get_template_part("parts/head"); ?>
```

- I undestood reusable components in wordpress which is very similar to react componets, or "template parts," for headers and footers. Using template parts improved both the maintainability and readability of the codebase, fulfilling the “Don’t Repeat Yourself” principle (DRY) and reinforcing the idea that modular design is essential for scalable web applications. For example, creating a template part for a header and reusing it across different pages saved a significant amount of repetitive code.

```
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->
```
  
 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- Initially, I attempted to create a theme using PHP-based templates, which was incompatible with WordPress’s modern block theme standards that rely on HTML templates and `theme.json` configurations

- I struggled with dynamically linking assets like images in my theme. Hardcoding paths was ineffective, as it limited the theme’s portability and made the structure less flexible.
  
```
<img src="<?php echo get_template_directory_uri(); ?>/assets/images/image.jpg" alt="Sample Image" />
```

- I faced the challenge in syncing the pattern I created in the WordPress dashboard. After initial registration, I discovered that changes in the theme files weren’t reflected without re-syncing, which led to difficulties in testing updates.

- I striggled adapting to WordPress’s use of comments as a form of configuration. In the hero block pattern, each block includes configuration details as JSON-like comments, which WordPress reads and interprets. This syntax is quite different from other environments I’ve worked in, where variable declarations and configurations are handled explicitly.

```
<!-- wp:cover {"url":"<?php echo esc_url(get_theme_file_uri('assets/images/hero-background.jpg')); ?>","dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull">
    <!-- Content here -->
</div>
```


## Feedback (For CF's)
> [**Course Facilitator name**]
 
Alexander

> [*What went well*]

Strong grasp of WordPress architecture demonstrated through proper configuration and theme development. Good understanding of modular design with template parts and block patterns. Clear code examples showing practical implementation of WordPress concepts.

> [*Even better if*]

Show how you resolved the asset linking issue instead of just identifying it. Since you mentioned the PHP-to-HTML template transition was a challenge, document the actual changes you made.

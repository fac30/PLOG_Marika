## Guidance
Answer the following questions considering the learning outcomes for
- [Week 014](https://learn.foundersandcoders.com/course/syllabus/developer/week14-TFB-build/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
- Developed a foundational understanding of how to structure a WordPress plugin. This included setting up the wsp-wordpress-plugin folder with subfolders for includes, css, and js, demonstrating good organisational practices for separating logic, styles, and scripts.

- The following code ensures the plugin cannot be directly accessed:
```
if (!defined('ABSPATH')) {
    exit;
}

```
- Implemented scripts and styles enqueueing for both the frontend and backend using `wp_enqueue_scripts` and `admin_enqueue_scripts`.
  
```
wp_enqueue_style('wsp-styles', plugin_dir_url(__FILE__) . 'css/styles.css', array(), '1.0.0');
wp_enqueue_script('wsp-scripts', plugin_dir_url(__FILE__) . 'js/scripts.js', array('jquery'), '1.0.0', true);
```
- The `wp_enqueue_scripts` action hook is used to include JavaScript and CSS files in the plugin. It takes a hook name (`wp_enqueue_scripts`) and a callback function (`wsp_enqueue_assets`).
- Enqueue means scheduling an item (e.g., styles or scripts) to load at the appropriate time and place on the frontend. Inside the callback function, we can also attach dependencies.
- For backend assets, a similar process is followed using the `admin_enqueue_scripts` action hook.
```
function wsp_enqueue_admin_assets($hook) {
    if ($hook !== 'settings_page_wsp-plugin-settings') {
        return;
    }
    wp_enqueue_style('wsp-admin-styles', plugin_dir_url(__FILE__) . 'css/admin-styles.css', array(), '1.0.0');
    wp_enqueue_script('wsp-admin-scripts', plugin_dir_url(__FILE__) . 'js/admin-scripts.js', array('jquery'), '1.0.0', true);
}
add_action('admin_enqueue_scripts', 'wsp_enqueue_admin_assets');
```
- Created an admin settings page to configure plugin options using `add_options_page`. This involved defining a callback to render HTML for the settings page.
```
function wsp_add_settings_page() {
    add_options_page(
        'Plugin Name settings',
        'Plugin Name',
        'manage_options',
        'wsp-plugin-settings',
        'wsp_render_settings_page'
    );
}
add_action('admin_menu', 'wsp_add_settings_page');
 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
```
- The `admin_menu hook` is used to attach submenus in the admin panel menu (WordPress dashboard).
<img width="337" alt="Screenshot 2024-12-13 at 14 51 43" src="https://github.com/user-attachments/assets/3a7cfd96-ffba-4380-af3a-c768e17b023f" />


  
- Functions like `esc_html__()` are used within the settings page to identify the plugin and translate strings into other languages, ensuring accessibility and internationalisation.

- Creating a Plugin for Header and Footer Code Injection. Key Features Implemented:
- Admin menu for plugin settings (`add_menu_page()`).
- Settings page with input fields for header and footer code.
- Meta boxes for custom code per post type.
- Sanitization of user inputs using `wp_kses()`.

- `get_option()` function retrieve and inject saved header and footer code dynamically into the WordPress theme using `wp_head` and `wp_footer`.
```
function wsp_inject_header_code() {
    $header_code = get_option('wsp_header_code');
    if (!empty($header_code)) {
        echo $header_code;
    }
}
add_action('wp_head', 'wsp_inject_header_code');

function wsp_inject_footer_code() {
    $footer_code = get_option('wsp_footer_code');
    if (!empty($footer_code)) {
        echo $footer_code;
    }
}
add_action('wp_footer', 'wsp_inject_footer_code');
```

- Implemented custom meta boxes for post-specific header and footer code, allowing users to inject unique code for individual posts/pages.
```
function wsp_add_custom_meta_boxes() {
    $post_types = get_post_types();
    foreach ($post_types as $post_type) {
        add_meta_box(
            'wsp_header_code_meta',
            'Header Code',
            'wsp_header_code_meta_box_callback',
            $post_type,
            'normal',
            'high'
        );
        add_meta_box(
            'wsp_footer_code_meta',
            'Footer Code',
            'wsp_footer_code_meta_box_callback',
            $post_type,
            'normal',
            'high'
        );
    }
}
add_action('add_meta_boxes', 'wsp_add_custom_meta_boxes');
```
<img width="420" alt="Screenshot 2024-12-13 at 14 51 50" src="https://github.com/user-attachments/assets/9e2fc030-5dbf-4d88-9775-09c8c10e85ee" />

> [**Learning outcome...**]  
> [your evidence here]

## Feedback (For CF's)
> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]

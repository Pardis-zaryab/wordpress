<?php
/**
 * Register meta boxes
 *
 * @package Farimand
 */

namespace FARIMAND_THEME\Inc;

use FARIMAND_THEME\Inc\Traits\Singleton;

class Meta_Boxes {
    use Singleton;

    protected function __construct()
    {
        // Load classes
        $this -> setup_hooks();
    }

    protected function setup_hooks()
    {
        /**
         * Actions.
         */
        add_action( 'add_meta_boxes', [ $this, 'add_custom_meta_box' ] );
    }

    public function add_custom_meta_box() {
        $screens = [ 'post'];
        foreach ( $screens as $screen ) {
            add_meta_box(
                'hide-page-title',                 // Unique ID
                __( 'Hide page title', 'farimand' ),      // Box title
                [ $this, 'custom_meta_box_html' ],  // Content callback, must be of type callable
                $screen,                            // Post type
                'side'
            );
        }
    }

    public function custom_meta_box_html( $post ) {
        $value = get_post_meta( $post->ID, '_hide_page_title', true );
        ?>

        <label for="farimand-field"><?php esc_html_e( 'Hide the page title', 'farimand' ); ?></label>
        <select name="farimand_field" id="farimand-field" class="postbox">
            <option value=""><?php esc_html_e( 'Select', 'farimand' ); ?></option>
            <option value="yes" <?php selected( $value, 'yes' ); ?>>
                <?php esc_html_e( 'Yes', 'farimand' ); ?>
            </option>
            <option value="no" <?php selected( $value, 'no' ); ?>>
                <?php esc_html_e( 'No', 'farimand' ); ?>
            </option>
        </select>
        <?php
    }


}


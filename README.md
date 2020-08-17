# Woocommerce-cart-page-hide-qty
Woocommerce-cart-page-hide-qty
function hide_quantity_input_field_in_ultimate_product_cart_page( $args, $product ) {
    // $product_ids = array(11245,13959); // live server
    $product_ids = array(11245,11903); // Dev server
    $the_id = $product->is_type('variation') ? $product->get_parent_id() : $product->get_id();
    if( is_cart() && in_array( $the_id, $product_ids ) ){
        $input_value = $args['input_value'];
        $args['min_value'] = $args['max_value'] = $input_value;
    }
    return $args;
}
add_filter( 'woocommerce_quantity_input_args', 'hide_quantity_input_field_in_ultimate_product_cart_page', 20, 2 );

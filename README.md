function add_download_count(){
    global $product;
    if ($product->is_downloadable('yes')){
$query = "SELECT SUM( download_count ) AS count FROM {$wpdb->prefix}woocommerce_downloadable_product_permissions WHERE product_id = $product->id";
    $count = $wpdb->get_var( $query );
        echo "Downloads: ".$count;
    }
}
add_action("woocommerce_before_single_product_summary", "add_download_count");

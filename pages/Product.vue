<template>
<div>
<div class="container product-details">
  
    <div class="product-header-section">
    <div class="col-sm-6 col-md-5 col-lg-5 product-image-container">
    <div class="product">
      
        <SfGallery :images="productGallery" class="product__gallery"     enableZoom/>
     
    </div>
    </div>
   
    <div class="col-sm-6 col-md-6 col-lg-6 product-details-wrapper">
       <a href="/en/brands/bennett" class="product-brand">   <div  v-for="(props,index) in properties" :key="index">
								 <div v-if="index === 'Brand'" >
                 
                    {{ props.toString()}}
                 
                </div>
                  </div><span> Shop All &gt; </span></a>
       <div class="product-header-section">
        <div class="product__header">
          <h1 class="productdetails-title">
            <span  class= "new" v-for="(props,index) in properties" :key="index"> <span v-if="index === 'Brand'" >
                 
                    {{ props.toString()}}
                 
                </span>
            </span>
          <SfHeading
            :title="productGetters.getName(product)"
            :level="3"
            class="sf-heading--left"
          />
          </h1>
              <ul class="productdetails-detail">
              <li id="rating-tab">
                <div class="bv_main_container">
                  <div class="bv_main_container_row_flex">
                
                <SfRating :score="averageRating" :max="5"  />
              <a v-if="!!totalReviews" href="#" class="product__count">
                ({{ totalReviews }})
              </a>
                  </div>
            <!-- </div> -->
             <div class="bv_main_container_row_flex">
            <SfButton data-cy="product-btn_read-all" class="sf-button--text">{{
              $t('Write a review')
            }}</SfButton>
             </div>
             </div>
             
              <li>Item: #1076-108 </li>
            
                
                      
              <li>MODEL: #CTC</li>
              </ul>
            
          <!-- <h1 class="productdetails-title" v-bind:title="productGetters.getName(product)" /> -->
          <!-- <SfButton
            class="sf-button--pure sf-header__action on_wishList"
            v-if="isAuthenticated && isPurchasable"
            @click="
              !isInWishlist({ product })
                ? addItemToWishlist({ product })
                : removeItemFromWishlist({ product })
            "
          >
          
            <SfIcon
              class="sf-header__icon"
              :icon="currentWishlistIcon"
              size="1.25rem"
              data-test="sf-wishlist-icon"
            />
          </SfButton> -->
          <SfIcon
            icon="drag"
            size="xxl"
            color="var(--c-text-disabled)"
            class="product__drag-icon smartphone-only"
          />
        </div>
        <div class="product__price-and-rating">
          <SfPrice
            :regular="$n(productGetters.getPrice(product).regular, 'currency')"
            :special="
              productGetters.getPrice(product).special &&
                $n(productGetters.getPrice(product).special, 'currency')
            "
          />
          <div>
           
            
          <p class="environmental-handling-fee"> </p>
          <img class="aeroplan-miles-print" style="display:none" src="https://homehardware.sirv.com/resources/images/footer-logosR2.png" alt="Aeroplan Image">
          <p class="aeroplan-miles"><span class="link_txt"> Earn 5 Aeroplan Points  </span></p>
       
            
          </div>
        </div>
       </div>
       
           <div class="boh-info">
           <div class="col-xs-12 col-sm-12 col-md-12 no-padding">
                                <div class="boh-icon">
                                    <div class="img-responsive icon storeicon"></div>
                                    <h3 class="boh-msg">
                                        
                                        <span class="available-stock">
                                            
                                                2
                                            
                                        in stock at your store</span>
                                        
                                        <span class="info-icon popupover" data-toggle="popover" data-trigger="hover" data-content="<p class='store-disclaimer'>We always try our best to show you the most accurate in-store inventory. However, someone else may already have this item in their cart.</p><p class='pricing-offer'>Pricing and offers may vary by location</p>" data-original-title="" data-html="true" title="" data-placement="top"></span>
                                    </h3>
                                    <p><a href="#" class="link check-nearby" id="checkNearByStore">Check nearby stores</a></p>
                                </div>
                            </div>
</div>
<div class="button add">
<div class="mz-productdetails-quantity" id="quantityContainer">
  <!-- <div class="productdetail-conversion-controls">
        <label class="mz-qty-label" for="productQuantity">Order Quantity:</label>
        <div class="quantity-input"> <a href="javascript:;" class="link quantity-input-button decrement is-disabled " data-mz-value="qty-decrement" title="Quantity decreament"> <span class="material-icons qty-decrement">remove_circle</span> </a> <label for="product-qty" class="nofont">Please enter a product quantity above 0</label> <input id="product-qty" class="mz-productdetail-qty form-control" maxlength="3" type="text" value="1" min="1" data-mz-value="quantity" pattern="\d*"> <a href="javascript:;" class="link quantity-input-button" data-mz-value="qty-increment" title="Quantity increment"> <span class="material-icons qty-increment">add_circle</span> </a> </div>
        <span class="mz-validationmessage" data-mz-validationmessage-for="quantity"></span>
    </div> -->
    <div class="save-and-addtocart">
      <div class="save-add-buttoncontainer">
    <!-- <button id="add-to-cart" class="mz-productdetail-addtocart mz-button product-addtocart " data-mz-action="initiateAddToCart"> Add To Cart </button>
         </div>
          <div class="save-add-buttoncontainer">
      <button id="add-to-wishlist" class="mz-productdetail-addtowishlist mz-button product-savetolist btn-transparent" data-mz-action="addToWishlist">Save To List</button> -->
           <SfAddToCart
            data-cy="product-cart_add"
            :stock="stock"
            v-model="qty"
            :disabled="loading || !isPurchasable"
            :canAddToCart="stock > 0"
            class="product__add-to-cart"
            @click="addItem({ product, quantity: parseInt(qty) })"
          />
          </div>
      <!-- </div> -->
      </div>
</div>

</div>
<div class="product-location-availability">
<div class="icons">
                    <div class="img-responsive icon storeicon"></div>
                    <div class="information-container ">
                        <h4 class="icon-title">FREE In-Store Pick-up*</h4>
                        <p class="icon-text">
                            
                                <strong>Buy online, pick-up at</strong>
                            
                            <strong>Home Hardware - St. Jacobs</strong>
                        </p>
                        
                        <p class="get-it-by">Estimated Arrival: 2-15 days</p>
                        <p class="get-it-by">*on all eligible orders</p>
                        
                    </div>
                </div>
                
<div class="icons ship-to-home" id="shipToHomeContainer">
                    <div class="img-responsive icon deliveryicon"></div>
                    <div class="information-container">
                        <h4 class="icon-title">Ship to Home</h4>
                        <p class="icon-text">
                            <span class="available">
                                 
                                    Available
                                 
                            </span>
                            
                                for shipping to <strong>N0B2N0</strong>
                            
                        </p>
                        

                                    <p class="get-it-by">Estimated Arrival: 8-10 business days</p>
                                
                                <a class="change-shipping-location" data-mz-action="showEstimateShippingModal" href="javascript:void(0)"><b>Estimate Shipping Cost</b> </a>
                            
                            <div id="shipping-popup-container" class="ship-container"></div>
                        
                    </div>
                </div>
</div>


        </div>
          
          <!-- <p class="product__description desktop-only" v-html="description"></p> -->
         
        
         
          <SfSelect
            data-cy="product-select_size"
            v-if="options.size"
            :value="configuration.size"
            @input="(size) => updateFilter({ size })"
            label="Size"
            class="sf-select--underlined product__select-size"
            :required="true"
          >
            <SfSelectOption
              v-for="size in options.size"
              :key="size"
              :value="size"
            >
              {{ size }}
            </SfSelectOption>
          </SfSelect>
          <div
            v-if="options.color && options.color.length > 1"
            class="product__colors desktop-only"
          >
            <p class="product__color-label">{{ $t('Color') }}:</p>
            <SfColor
              data-cy="product-color_update"
              v-for="(color, i) in options.color"
              :key="i"
              :color="color"
              class="product__color"
              @click="updateFilter({ color })"
            />
          </div>
          <!-- <SfAddToCart
            data-cy="product-cart_add"
            :stock="stock"
            v-model="qty"
            :disabled="loading || !isPurchasable"
            :canAddToCart="stock > 0"
            class="product__add-to-cart"
            @click="addItem({ product, quantity: parseInt(qty) })"
          /> -->

         
           
             
        </div>
      

        
    </div>
    
  <div class="col-sm-12 col-md-12 col-lg-12  prod-description-container">
<h3 class="section-title  product-tab-header">
						<span class="mainTitle">More Like This</span>
					</h3>

<div class="product-information prod-info-new-layout">
    <LazyHydrate when-visible>
      <RelatedProducts
        :products="relatedProducts"
        :loading="relatedLoading"
       
      />
    </LazyHydrate>
</div>

  </div>

  <div class="col-sm-12 col-md-12 col-lg-12 prod-description-container">
    <h3 class="section-title product-tab-header header-margin">
						Product Overview
					</h3>
          <div class="DescriptionAndDetailsContainer">
				
								<div class="productdetails-specification">
						 <p class="product__description desktop-only" v-html="description"></p>
      <!-- <table class="table table-bordered">
  <thead>
    <tr>
     
      <th scope="col">First</th>
      <th scope="col">Last</th>
    
    </tr>
  </thead>
  <tbody>
    <tr v-for="(props,index) in properties" :key="index">
    
      
      <td>
   brandname

      <td>  <div v-if="index === 'Brand'" >
                 
                    {{ props }}
                 
                </div></td>
     
    </tr>
    
  </tbody>
</table> -->
					</div>
							
						</div>
					
          </div>

          

          <div class="row item page-section" data-title="Specification" id="specification">
				
				<div class="col-sm-12 col-md-12 col-lg-12 prod-description-container section-margin">
					<h3 class="section-title product-tab-header header-margin">
						Specifications
					</h3>
					<div class="productdetails-attributes description-container" id="mobileSpecification" aria-expanded="false">
						
						<table width="100%">
							
				
							
							<tbody  >
                <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 " >
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
                  <div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Brand'" >
                 
                    {{ index }}
                 
                </div>
                  </div></td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%" >
                  <div  v-for="(props,index) in properties" :key="index">
								 <div v-if="index === 'Brand'" >
                 
                    {{ props.toString()}}
                 
                </div>
                  </div></td>
                </tr>
								
								
						

							
							<tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Category'" >
                 
                    {{ index }}
                 
                </div>
               
                  </div></td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								 <div  v-for="(props,index) in properties" :key="index">
								 <div v-if="index === 'Category'" >
                 
                    {{ props.toString() }}
                 
                </div>
                  </div></td>
								
								
							</tr>
				
							
							
							<tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Assembled Product Length'" >
                 
                  {{index}}
                 
                </div>
                  </div></td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								 <div  v-for="(props,index) in properties" :key="index">
								 <div v-if="index === 'Assembled Product Length'" >
                 
                    {{ props.toString() }}
                 
                </div>
                
                  </div></td>
								
								
							</tr>
							
				
							
							<tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
                  
									<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Assembled Product Width'" >
                 
                  
                 {{index}}
                </div>
                  </div>
                
                	</td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Assembled Product Width'" >
                 
                    {{ props.toString() }}
                 
                </div>
                  </div></td>
								
								
							</tr>
						
							<tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Assembled Product Height'" >
                 
                  
                 {{index}}
                </div>
                  </div></td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Assembled Product Height'" >
                 
                  
                 {{props.toString()}}
                </div>
                  </div></td>
								
								
							</tr>
					
							<tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Model'" >
                 
                  
                 {{index}}
                </div>
                  </div></td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
								<div  v-for="(props,index) in properties" :key="index">
								<div v-if="index === 'Model'" >
                 
                  
                 {{props.toString()}}
                </div></div></td>
								
								
							</tr>
							
					
							<!-- <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12 ">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Category</td>
								
								
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Electric &amp; Space Heaters</td>
								
								
							</tr> -->

							
							<!-- <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Package Weight</td>
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									6.40
									lbs</td>
							</tr> -->
							<!-- <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Package Length</td>
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									1.00
									in</td>
							</tr> -->
							<!-- <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Package Width</td>
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									1.00
									in</td>
							</tr> -->

							<!-- <tr class="attributes col-lg-6 col-md-6 col-sm-6 col-xs-12">
								<td class="attribute-title col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									Package Height</td>
								<td class="attribute-value col-lg-6 col-md-6 col-sm-6 col-xs-6" width="50%">
									1.00
									in</td>
							</tr> -->
							
								
							<tr class="attributes">
								
							</tr>
							
						</tbody></table>
						
					</div>
				</div>
				
			</div>
      
            
  </div>

</template>
<script>
import {
  SfProperty,
  SfHeading,
  SfPrice,
  SfRating,
  SfSelect,
  SfAddToCart,
  SfRadio,
  SfTabs,
  SfGallery,
  SfIcon,
  SfImage,
  SfBanner,
  SfAlert,
  SfSticky,
  SfReview,
  SfBreadcrumbs,
  SfButton,
  SfColor,
} from '@storefront-ui/vue';

import InstagramFeed from '~/components/InstagramFeed.vue';
import RelatedProducts from '~/components/RelatedProducts.vue';
import { ref, computed } from '@vue/composition-api';
import {
  useProduct,
  useWishlist,
  useCart,
  productGetters,
  useReview,
  reviewGetters,
  useUser,
} from '@vue-storefront/kibocommerce';
import { onSSR } from '@vue-storefront/core';
import MobileStoreBanner from '~/components/MobileStoreBanner.vue';
import LazyHydrate from 'vue-lazy-hydration';

export default {
  name: 'Product',
  transition: 'fade',
  props: {
    wishlistIcon: {
      type: [String, Array, Boolean],

      default: 'heart',
    },

    isOnWishlistIcon: {
      type: [String, Array],

      default: 'heart_fill',
    },
  },
  setup(props, context) {
    const qty = ref(1);
    const { id } = context.root.$route.params;
    const { isAuthenticated } = useUser();
    const {
      load: loadWishlist,
      addItem: addItemToWishlist,
      isInWishlist,
      removeItem: removeItemFromWishlist,
    } = useWishlist();
    const { products, search } = useProduct('products');
    const {
      products: relatedProducts,
      search: searchRelatedProducts,
      loading: relatedLoading,
    } = useProduct('relatedProducts');
    const { addItem, loading } = useCart();
    const { reviews: productReviews, search: searchReviews } =
      useReview('productReviews');

    const product = computed(() => products.value);

    const currentWishlistIcon = computed(() => {
      return isInWishlist({ product: product.value })
        ? props.isOnWishlistIcon
        : props.wishlistIcon;
    });

    const options = computed(() => productGetters.getOptions(product.value));
    const configuration = computed(() =>
      productGetters.getConfiguration(product.value)
    );
    const categories = computed(() =>
      productGetters.getCategoryIds(product.value)
    );
    const reviews = computed(() =>
      reviewGetters.getItems(productReviews.value)
    );
    const description = computed(() =>
      productGetters.getDescription(product.value)
    );
    const brandname = computed(() =>
      productGetters.getBrandname(product.value)
    );
    const properties = computed(() =>
      productGetters.getAttributes(product.value)
    );
    const breadcrumbs = computed(() =>
      productGetters.getBreadcrumbs(product.value)
    );

    const productGallery = computed(() =>
      productGetters.getGallery(product.value).map((img) => ({
        mobile: { url: img.small },
        desktop: { url: img.normal },
        big: { url: img.big },
        alt: productGetters.getName(product.value),
      }))
    );

    onSSR(async () => {
      await Promise.all([
        loadWishlist(),
        search({ id, attributes: context.root.$route.query }),
        searchRelatedProducts({
          catId: [categories.value[0]],
          limit: 8,
          id,
        }),
        searchReviews({ productId: id }),
      ]);
    });

    const updateFilter = (filter) => {
      context.root.$router.push({
        path: context.root.$route.path,
        query: {
          ...configuration.value,
          ...filter,
        },
      });
    };

    return {
      updateFilter,
      configuration,
      isInWishlist,
      product,
      reviews,
      reviewGetters,
      averageRating: computed(() =>
        productGetters.getAverageRating(product.value)
      ),
      totalReviews: computed(() =>
        productGetters.getTotalReviews(product.value)
      ),
      relatedProducts: computed(() =>
        productGetters.getFiltered(relatedProducts.value, { master: true })
      ),
      relatedLoading,
      options,
      qty,
      addItem,
      loading,
      productGetters,
      productGallery,
      description,
      brandname,
      properties,
      breadcrumbs,
      isAuthenticated,
      isPurchasable: computed(() =>
        productGetters.getPurchasable(product.value)
      ),
      stock: computed(() => productGetters.getInventory(product.value)),
      addItemToWishlist,
      removeItemFromWishlist,
      currentWishlistIcon,
    };
  },
  components: {
    SfAlert,
    SfColor,
    SfProperty,
    SfHeading,
    SfPrice,
    SfRating,
    SfSelect,
    SfAddToCart,
    SfRadio,
    SfTabs,
    SfGallery,
    SfIcon,
    SfImage,
    SfBanner,
    SfSticky,
    SfReview,
    SfBreadcrumbs,
    SfButton,
    InstagramFeed,
    RelatedProducts,
    MobileStoreBanner,
    LazyHydrate,
  },
  data() {
    return {};
  },
};
</script>

<style >
@import '//fonts.googleapis.com/css?family=Work+Sans:400,500,700';
@import '//cdnjs.cloudflare.com/ajax/libs/material-design-iconic-font/2.2.0/css/material-design-iconic-font.min.css';
@import '//hh-styleguide.s3.ca-central-1.amazonaws.com/css/bootstrap3.7.css';
@import '//hh-styleguide.s3.ca-central-1.amazonaws.com/css/app.css';
@import '//hh-styleguide.s3.ca-central-1.amazonaws.com/css/utilities.css';
.sf-add-to-cart {
  --button-background: #e4002b;
  --button-font-family: Agenda, sans-serif;

  --button-border-radius: 22px;
  width: 200%;
}
.sf-heading__title {
  --heading-title-font-weight: 3.4rem;
  --heading-title-font-size: 3.4rem;
}
.sf-price__regular {
  --price-regular-font-size: 3.4rem;
  --price-regular-font-family: 'Agenda_bold', sans-serif;
}
.productdetails-detail {
  list-style-type: none;
  padding: 0px;
}
.productdetails-title {
  font-size: 3.4rem;
  margin: 0 0 20px;
  font-weight: 500;
  line-height: 1.1;
  font-family: sans-serif;
}
.DescriptionAndDetailsContainer {
  width: 1120px;
  margin: 0 auto;
  margin-bottom: 40px;
}
.bv_main_container {
  display: flex;

  flex-direction: row;
  justify-content: flex-start;
  column-gap: 20px;
}
.boh-info {
  border-bottom: 1px solid #c7c7c7;
  margin-bottom: 15px;
  float: left;
  width: 100%;
}
.product-header-section {
  overflow: hidden;
  border-bottom: 1px solid #c7c7c7;
  margin-bottom: 15px;
}
.save-and-addtocart {
  display: flex;
  margin-bottom: 0;
  padding-bottom: 20px;
  width: 100%;
}
#add-to-cart {
  background-color: #e4002b;
  border: 2px solid #e4002b;
  color: #fff;
  width: 100%;
  display: block;
  border-radius: 22px;
  font-family: Agenda, sans-serif;
  font-size: 18px;
  font-weight: 600;
  letter-spacing: 0;
  line-height: 18px;
  text-decoration: none;
  text-transform: capitalize;
  padding: 12px 22px;
}
#add-to-wishlist {
  width: 100%;
  display: block;
  box-sizing: border-box;
  border: 2px solid #e4002b;
  border-radius: 22px;
  font-family: Agenda, sans-serif;
  font-size: 18px;
  font-weight: 600;
  letter-spacing: 0;
  line-height: 18px;
  text-align: center;
  color: #e4002b;
  background-color: #fff;
  text-decoration: none;
  text-transform: capitalize;
  padding: 12px 22px;
  padding-left: 0;
  padding-right: 0;
}
.save-add-buttoncontainer {
  display: flex;
  width: 70%;
}
.sf-product-card__title {
  --product-card-title-font-family: 'Agenda', sans-serif;
  min-height: 35px;
  --product-card-title-font-size: 16px;
}
.sf-arrow {
  --button-background: #e4002b;
  --icon-color: white;
}

.icon.deliveryicon {
    width: 66px;
}
.boh-icon .icon {
    height: 40px;
    position: absolute;
    top: 0;
    left: 0;
}
.boh-msg{
padding-left: 63px;
}
.check-nearby{
  padding-left: 63px;
}
 .deliveryicon {
 
    
    background-image: url('https://homehardware-uat.sirv.com/resources/images/Web-Icons-on-one-file.png');
    background-size: 159px;
    background-position: -5px -445px;
}
.information-container {
    padding-left: 76px;
}

.icons {
  border-bottom: 1px solid #c7c7c7;
  padding: 15px 0;
}
.icons ship-to-home {
  border-bottom: 1px solid #c7c7c7;
  padding: 15px 0;
  box-sizing: border-box;
}
.icon {
    width: 53px;
    height: 41px;
    float: left;
}
.storeicon {
  width: 58px;
  background-image: url('https://homehardware-uat.sirv.com/resources/images/Web-Icons-on-one-file.png');
  background-size: 150px;
  background-position: 61px -418px;
}
.img-responsive {
  display: block;
  max-width: 100%;
 
}
.link {
  font-size: 1.6rem;
  color: #e4002b;
  text-decoration: none;
}
.new{
      font-family: "Agenda_bold",sans-serif;
    font-style: normal;
    font-weight: normal;
}
.check-nearby {
  cursor: pointer;
  font-family: 'Agenda_bold', sans-serif;
  font-style: normal;
  font-weight: bold;
}
.product-brand {
  font-family: "Agenda_bold",sans-serif;
    font-style: normal;
    font-weight: normal;
    text-transform: uppercase;
    margin-top: 0;
    color: #e4002b;
    display: flex;
}
.product-brand span {
  cursor: pointer;
  font-family: 'Agenda', sans-serif !important;
  color: #3f3f3f !important;
  text-transform: capitalize;
  padding-left: 15px;
}
.product-image-container {
  position: relative;
  min-height: 1px;
  padding-left: 15px;
  padding-right: 15px;
}
.product-tab-header {
  padding: 10px 0px 0px 10px;
  margin-top: 6px;
  text-transform: capitalize;
  border-bottom: 1px solid #c5c5c5;
}
.section-title {
  font-size: 4rem;
}
.attributes {
  width: 50%;
  margin-bottom: 0px;
  border: 1px solid #c5c5c5;
  padding: 0;
}
.attribute-title {
  margin: 0px;
  background: #e6e6e6;
  padding: 13px;
  font-family: 'Agenda_bold', sans-serif;
  display: block;
  float: left;
  font-size: 1.6rem;
}
.attribute-value {
  margin: 0px;
  padding: 10px;
  display: block;
  float: left;
}
.description-container {
  padding: 0 15px;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
  border-color: grey;
}
tbody {
  display: table-row-group;
  vertical-align: middle;
  box-sizing: border-box;
}


/* .save-add{
      padding-right: 5px;
} */
</style>

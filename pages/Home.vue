<template>
  <div id="home">
    <div class="new">
  <div class="Rectangle-723">
 
  </div>
   <div class= "Shope_by">
    <p>Shope_by</p>

  </div>
  <div class="check_more">

   
   <div class="grid1">
     <div class="container">
     <img src="homepage/mask-group-12.svg"
     class="Mask-Group-12">
<div class="New-collection-available-now">
  New collection
available now
</div><button class="CHECK-MORE"><span class="check-more-font"> CHECK MORE</span> </button>
     </div>
   </div>
 
 <div class="grid2"><span class="New-collection-available-now">
  Redefining the
modern design
</span><button class="CHECK-MORE"><span class="check-more-font"> CHECK MORE</span> </button></div>
  </div>
  </div>
   
  </div>
</template>
<script>
import {
  SfHero,
  SfBanner,
  SfCallToAction,
  SfSection,
  SfCarousel,
  SfProductCard,
  SfImage,
  SfBannerGrid,
  SfHeading,
  SfArrow,
  SfButton
} from '@storefront-ui/vue';
import { useContent, contentGetters } from '@vue-storefront/kibocommerce';
import { onSSR } from '@vue-storefront/core';
import { computed} from '@vue/composition-api';
import InstagramFeed from '~/components/InstagramFeed.vue';
import MobileStoreBanner from '~/components/MobileStoreBanner.vue';
import LazyHydrate from 'vue-lazy-hydration';

export default {
  name: 'Home',
  components: {
    InstagramFeed,
    SfHero,
    SfBanner,
    SfCallToAction,
    SfSection,
    SfCarousel,
    SfProductCard,
    SfImage,
    SfBannerGrid,
    SfHeading,
    SfArrow,
    SfButton,
    MobileStoreBanner,
    LazyHydrate
  },
  setup() {
    const { search: loadBanners, content: contentBanners} = useContent('Banners');
    const { search: loadHeros, content: contentHeroes} = useContent('Heros');

    onSSR(async () => {
      await loadHeros({ documentType: 'hero_images@mozu', slug: 'home'});
      await loadBanners({ documentType: 'banners@mozu', slug: 'home'});
    });
    const heroes = computed(() => getContent(contentHeroes.value, 'hero_images'));
    const banners = computed(() => getContent(contentBanners.value, 'banners'));

    function toggleWishlist(index) {
      this.products[index].isInWishlist = !this.products[index].isInWishlist;
    }

    function getContent(content, type) {
      return contentGetters.getContent(content, type);
    }

    return {
      toggleWishlist,
      heroes: heroes,
      banners: banners,
      products: [
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productA.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: true
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productB.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productC.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productA.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productB.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productC.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productA.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        },
        {
          title: 'Cream Beach Bag',
          image: '/homepage/productB.webp',
          price: { regular: '50.00 $' },
          rating: { max: 5, score: 4 },
          isInWishlist: false
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>

.Rectangle-723 {
   box-sizing: border-box;

 
  width: 1250px;
  height: 332px;
  margin: 50px 0;
  padding: 31.7px 624px 59.7px 100px;
  opacity: 0.4;
  background-color: #000;
}
.new{
  padding-left: none;
}
.Shope_by{
  width: 1240px;
  height: 424px;
   border: 1px solid blue;
}
.check_more{
    display: grid;
     
}
.check-more-font{
 width: 91px;
  height: 20px;
  font-family: 'Poppins';
   //src: url(https://fonts.gstatic.com/s/poppins/v15/pxiByp8kv8JHgFVrLBT5Z11lFd2JQEl8qw.woff2) format('woff2');
  font-size: 14px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.5;
  letter-spacing: normal;
  text-align: left;
  color: #fff;
}
.CHECK-MORE{
    width: 152px;
  height: 41px;
  margin: 30px 30px 76px 67px;
  //padding: 11px 30px 10px 31px;
  border-radius: 6px;
  background-color: #8959fa;
}
// .Mask-Group-12{
//   width: 310px;
//   height: 268px;
//   margin: 0 42px 0 0;
// }
.New-collection-available-now {
  width: 183px;
  height: 70px;
  margin: 51px 0 30px 67px;
  font-family: 'Poppins';
  font-size: 25px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: 1.4;
  letter-spacing: normal;
  text-align: left;
  color: #3c3c3c;
}

.grid1{
  display: grid;
      //position: relative;
  //text-align: center;
    //border: 1px solid blue;
   grid-column: 1 / 2;
   grid-row: 1;
    width: 640px;
   height: 327px;
     justify-content: end;
     background-color: 	#dada07;
}
.grid2{
     
    //border: 1px solid blue;
      width: 598px;
  height: 327px;
    grid-column: 2 / 2;
   grid-row: 1;
    display: grid;
     justify-content: end;
}

</style>
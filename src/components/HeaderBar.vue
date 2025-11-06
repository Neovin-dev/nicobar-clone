<template>
    <header id="section-header" class="flex w-full sticky top-0 bg-white z-2">
        <!-- Header element starts -->
        <div class="Header-Wrapper">
            <section class="nav swiper">
                <div class="menu-wrapper-top flex items-center justify-between">
                    <div class="header-left flex">
                        <div class="header-burger-menu w-4">
                        <button class="left-burger-menu">
                            <span class="burger-icon ">
                                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="19" viewBox="0 0 24 19" fill="none">
                                    <g filter="url(#filter0_d_1029_1532)">
                                    <rect x="2" y="1.25781" width="20" height="1" fill="white"></rect>
                                    <rect x="1.9" y="1.15781" width="20.2" height="1.2" stroke="white" stroke-width="0.2"></rect>
                                    </g>
                                    <g filter="url(#filter1_d_1029_1532)">
                                    <rect x="2" y="8.64258" width="20" height="1" fill="white"></rect>
                                    <rect x="1.9" y="8.54258" width="20.2" height="1.2" stroke="white" stroke-width="0.2"></rect>
                                    </g>
                                    <g filter="url(#filter2_d_1029_1532)">
                                    <rect x="2" y="16.0273" width="20" height="1" fill="white"></rect>
                                    <rect x="1.9" y="15.9273" width="20.2" height="1.2" stroke="white" stroke-width="0.2"></rect>
                                    </g>
                                    <defs>
                                    <filter id="filter0_d_1029_1532" x="0.799805" y="0.0585938" width="22.4004" height="3.39844" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                        <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                        <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                        <feOffset></feOffset>
                                        <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                        <feComposite in2="hardAlpha" operator="out"></feComposite>
                                        <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                        <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1532"></feBlend>
                                        <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1532" result="shape"></feBlend>
                                    </filter>
                                    <filter id="filter1_d_1029_1532" x="0.799805" y="7.44336" width="22.4004" height="3.39844" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                        <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                        <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                        <feOffset></feOffset>
                                        <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                        <feComposite in2="hardAlpha" operator="out"></feComposite>
                                        <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                        <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1532"></feBlend>
                                        <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1532" result="shape"></feBlend>
                                    </filter>
                                    <filter id="filter2_d_1029_1532" x="0.799805" y="14.8281" width="22.4004" height="3.39844" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                        <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                        <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                        <feOffset></feOffset>
                                        <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                        <feComposite in2="hardAlpha" operator="out"></feComposite>
                                        <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                        <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1532"></feBlend>
                                        <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1532" result="shape"></feBlend>
                                    </filter>
                                    </defs>
                                </svg>
                            </span>
                        </button>
                    </div>

                    <div @click="reloadPage" class="header-logo pl-2 flex align-middle">
                        <div class="logo">
                            <a href="#">
                                <span class="svg-logo-wrap"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 414 63"><g fill="#2f343e"><path data-name="Path 1" d="M6.273 29.546v24.306H0v-38.42L25.875 40V15.955h6.273v38.42z"></path><path data-name="Path 2" d="M69.784 2.116h6.011v37.9h-6.272v-37.9z"></path><path data-name="Path 3" d="M107.42 35.034a19.133 19.133 0 0119.341-19.341 17.738 17.738 0 0113.33 5.489l-3.92 4.443a12.425 12.425 0 00-9.409-3.92c-7.58 0-13.068 6.011-13.068 13.591s5.75 13.591 13.068 13.591a13.448 13.448 0 009.409-3.92l3.92 4.443a17.738 17.738 0 01-13.33 5.483c-10.716-.518-19.341-8.882-19.341-19.859z"></path><path data-name="Path 4" d="M183.739 20.41a19.3706811 19.3706811 0 1138.685-2.089 19.174 19.174 0 01-18.3 20.389 18.99 18.99 0 01-20.385-18.3zm32.409-1.568c-.524-7.578-6.273-13.332-13.852-12.805a12.876 12.876 0 00-12.285 14.113c.523 7.58 6.273 13.33 13.852 12.807 7.58-.261 12.808-6.534 12.285-14.114z"></path><path data-name="Path 5" d="M261.102 14.322h13.33c6.8 0 11.239 4.7 11.239 10.455a8.166 8.166 0 01-3.659 7.318 9.588 9.588 0 016.011 9.409c0 6.534-5.227 10.977-12.546 10.977h-14.636V14.322zm12.807 15.943c3.92 0 5.75-2.352 5.75-5.227s-1.83-5.227-5.75-5.227h-6.534v10.193h6.534zm1.83 16.2c4.182 0 6.273-2.352 6.273-5.489s-2.091-5.484-6.271-5.484h-8.364V46.47z"></path><path data-name="Path 6" d="M335.591 1.332l18.557 38.42h-6.8l-3.914-8.363h-15.945l-3.921 8.364h-6.534zm-6.011 24.307h10.454L334.807 14.4z"></path><path data-name="Path 7" d="M395.443 33.04h-3.659v16.2h-6.273V11.085h12.284c7.057 0 12.023 4.443 12.023 10.977a10.9 10.9 0 01-7.841 10.455L414 49.244h-7.319zm1.83-5.489c4.182 0 6.273-2.091 6.273-5.227s-2.091-5.489-6.273-5.489h-5.489v10.716z"></path><path data-name="Path 8" d="M204.643 57.512L184 44.182l-18.557 12.284v5.75L184 49.932 204.643 63l18.3-12.018v-5.75z"></path></g></svg></span>
                            </a>
                        </div>
                    </div>
                    </div>

                    <div class="header-right">
                        
                    </div>
                    <div class="right-side-icon flex gap-10">
                        <span class="search-icon " @click="$emit('enable-search-bar')">
                            <svg xmlns="http://www.w3.org/2000/svg" width="19" height="20" viewBox="0 0 20 19" fill="none">
                                <g filter="url(#filter0_d_1029_1556)">
                                    <mask id="path-1-outside-1_1029_1556" maskUnits="userSpaceOnUse" x="0.958984" y="0.208984" width="18" height="18" fill="black">
                                    <rect fill="white" x="0.958984" y="0.208984" width="18" height="18"></rect>
                                    <path fill-rule="evenodd" clip-rule="evenodd" d="M13.7163 7.58766C13.7163 10.5582 11.3082 12.9663 8.33766 12.9663C5.3671 12.9663 2.95898 10.5582 2.95898 7.58766C2.95898 4.6171 5.3671 2.20898 8.33766 2.20898C11.3082 2.20898 13.7163 4.6171 13.7163 7.58766ZM12.8481 12.0981C11.6938 13.2524 10.0991 13.9663 8.33766 13.9663C4.81481 13.9663 1.95898 11.1105 1.95898 7.58766C1.95898 4.06481 4.81481 1.20898 8.33766 1.20898C11.8605 1.20898 14.7163 4.06481 14.7163 7.58766C14.7163 9.2983 14.0429 10.8517 12.9468 11.9971L13.5499 11.3857L18.5971 16.3647L17.8948 17.0766L12.8481 12.0981Z"></path>
                                    </mask>
                                    <path fill-rule="evenodd" clip-rule="evenodd" d="M13.7163 7.58766C13.7163 10.5582 11.3082 12.9663 8.33766 12.9663C5.3671 12.9663 2.95898 10.5582 2.95898 7.58766C2.95898 4.6171 5.3671 2.20898 8.33766 2.20898C11.3082 2.20898 13.7163 4.6171 13.7163 7.58766ZM12.8481 12.0981C11.6938 13.2524 10.0991 13.9663 8.33766 13.9663C4.81481 13.9663 1.95898 11.1105 1.95898 7.58766C1.95898 4.06481 4.81481 1.20898 8.33766 1.20898C11.8605 1.20898 14.7163 4.06481 14.7163 7.58766C14.7163 9.2983 14.0429 10.8517 12.9468 11.9971L13.5499 11.3857L18.5971 16.3647L17.8948 17.0766L12.8481 12.0981Z" fill="white"></path>
                                    <path d="M12.8481 12.0981L12.9885 11.9557L12.8471 11.8162L12.7066 11.9566L12.8481 12.0981ZM12.9468 11.9971L12.8023 11.8589L13.0892 12.1376L12.9468 11.9971ZM13.5499 11.3857L13.6904 11.2434L13.548 11.1029L13.4075 11.2453L13.5499 11.3857ZM18.5971 16.3647L18.7395 16.5052L18.8799 16.3628L18.7375 16.2223L18.5971 16.3647ZM17.8948 17.0766L17.7543 17.219L17.8967 17.3595L18.0372 17.2171L17.8948 17.0766ZM8.33766 13.1663C11.4187 13.1663 13.9163 10.6687 13.9163 7.58766H13.5163C13.5163 10.4478 11.1978 12.7663 8.33766 12.7663V13.1663ZM2.75898 7.58766C2.75898 10.6687 5.25664 13.1663 8.33766 13.1663V12.7663C5.47756 12.7663 3.15898 10.4478 3.15898 7.58766H2.75898ZM8.33766 2.00898C5.25664 2.00898 2.75898 4.50664 2.75898 7.58766H3.15898C3.15898 4.72756 5.47756 2.40898 8.33766 2.40898V2.00898ZM13.9163 7.58766C13.9163 4.50664 11.4187 2.00898 8.33766 2.00898V2.40898C11.1978 2.40898 13.5163 4.72756 13.5163 7.58766H13.9163ZM8.33766 14.1663C10.1543 14.1663 11.7992 13.4298 12.9895 12.2395L12.7066 11.9566C11.5883 13.075 10.0439 13.7663 8.33766 13.7663V14.1663ZM1.75898 7.58766C1.75898 11.221 4.70436 14.1663 8.33766 14.1663V13.7663C4.92527 13.7663 2.15898 11 2.15898 7.58766H1.75898ZM8.33766 1.00898C4.70436 1.00898 1.75898 3.95436 1.75898 7.58766H2.15898C2.15898 4.17527 4.92527 1.40898 8.33766 1.40898V1.00898ZM14.9163 7.58766C14.9163 3.95436 11.971 1.00898 8.33766 1.00898V1.40898C11.75 1.40898 14.5163 4.17527 14.5163 7.58766H14.9163ZM13.0913 12.1354C14.2216 10.9542 14.9163 9.35185 14.9163 7.58766H14.5163C14.5163 9.24474 13.8643 10.7491 12.8023 11.8589L13.0913 12.1354ZM13.0892 12.1376L13.6923 11.5262L13.4075 11.2453L12.8044 11.8567L13.0892 12.1376ZM13.4095 11.5281L18.4566 16.5071L18.7375 16.2223L13.6904 11.2434L13.4095 11.5281ZM18.4547 16.2243L17.7524 16.9362L18.0372 17.2171L18.7395 16.5052L18.4547 16.2243ZM18.0353 16.9342L12.9885 11.9557L12.7076 12.2404L17.7543 17.219L18.0353 16.9342Z" fill="white" mask="url(#path-1-outside-1_1029_1556)"></path>
                                </g>
                                <defs>
                                    <filter id="filter0_d_1029_1556" x="0.758789" y="0.00976562" width="19.1211" height="18.3496" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                    <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                    <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                    <feOffset></feOffset>
                                    <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                    <feComposite in2="hardAlpha" operator="out"></feComposite>
                                    <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                    <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1556"></feBlend>
                                    <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1556" result="shape"></feBlend>
                                    </filter>
                                </defs>
                                </svg>
                        </span>
                        <span class="profile-icon ">
                            <svg xmlns="http://www.w3.org/2000/svg" width="19" height="20" viewBox="0 0 19 20" fill="none">
                            <g filter="url(#filter0_d_1029_1560)">
                                <mask id="path-1-outside-1_1029_1560" maskUnits="userSpaceOnUse" x="0.59668" y="0.707031" width="18" height="19" fill="black">
                                <rect fill="white" x="0.59668" y="0.707031" width="18" height="19"></rect>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M5.59668 6.20703C5.59668 4.31842 7.29887 2.70703 9.50268 2.70703C11.7065 2.70703 13.4087 4.31842 13.4087 6.20703C13.4087 8.09564 11.7065 9.70703 9.50268 9.70703C7.29887 9.70703 5.59668 8.09564 5.59668 6.20703ZM9.50268 1.70703C6.83975 1.70703 4.59668 3.67736 4.59668 6.20703C4.59668 8.43908 6.34299 10.2357 8.58318 10.6275C4.67064 11.0587 1.59668 14.2074 1.59668 18.0771C1.59668 18.3533 1.82054 18.5771 2.09668 18.5771H16.9087C17.1848 18.5771 17.4087 18.3533 17.4087 18.0771C17.4087 14.2074 14.3347 11.0587 10.4222 10.6275C12.6624 10.2357 14.4087 8.43907 14.4087 6.20703C14.4087 3.67736 12.1656 1.70703 9.50268 1.70703ZM9.50268 11.5771C13.1625 11.5771 16.1177 14.243 16.3884 17.5771H2.61691C2.88764 14.243 5.84289 11.5771 9.50268 11.5771Z"></path>
                                </mask>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M5.59668 6.20703C5.59668 4.31842 7.29887 2.70703 9.50268 2.70703C11.7065 2.70703 13.4087 4.31842 13.4087 6.20703C13.4087 8.09564 11.7065 9.70703 9.50268 9.70703C7.29887 9.70703 5.59668 8.09564 5.59668 6.20703ZM9.50268 1.70703C6.83975 1.70703 4.59668 3.67736 4.59668 6.20703C4.59668 8.43908 6.34299 10.2357 8.58318 10.6275C4.67064 11.0587 1.59668 14.2074 1.59668 18.0771C1.59668 18.3533 1.82054 18.5771 2.09668 18.5771H16.9087C17.1848 18.5771 17.4087 18.3533 17.4087 18.0771C17.4087 14.2074 14.3347 11.0587 10.4222 10.6275C12.6624 10.2357 14.4087 8.43907 14.4087 6.20703C14.4087 3.67736 12.1656 1.70703 9.50268 1.70703ZM9.50268 11.5771C13.1625 11.5771 16.1177 14.243 16.3884 17.5771H2.61691C2.88764 14.243 5.84289 11.5771 9.50268 11.5771Z" fill="white"></path>
                                <path d="M8.58318 10.6275L8.60509 10.8263C8.70405 10.8154 8.77993 10.7334 8.78308 10.6338C8.78624 10.5343 8.71572 10.4477 8.61764 10.4305L8.58318 10.6275ZM10.4222 10.6275L10.3877 10.4305C10.2896 10.4477 10.2191 10.5343 10.2223 10.6338C10.2254 10.7334 10.3013 10.8154 10.4003 10.8263L10.4222 10.6275ZM16.3884 17.5771V17.7771C16.4443 17.7771 16.4976 17.7538 16.5355 17.7127C16.5733 17.6717 16.5923 17.6166 16.5878 17.561L16.3884 17.5771ZM2.61691 17.5771L2.41757 17.561C2.41304 17.6166 2.43201 17.6717 2.46988 17.7127C2.50774 17.7538 2.56105 17.7771 2.61691 17.7771V17.5771ZM9.50268 2.50703C7.20628 2.50703 5.39668 4.19091 5.39668 6.20703H5.79668C5.79668 4.44593 7.39147 2.90703 9.50268 2.90703V2.50703ZM13.6087 6.20703C13.6087 4.19091 11.7991 2.50703 9.50268 2.50703V2.90703C11.6139 2.90703 13.2087 4.44593 13.2087 6.20703H13.6087ZM9.50268 9.90703C11.7991 9.90703 13.6087 8.22315 13.6087 6.20703H13.2087C13.2087 7.96813 11.6139 9.50703 9.50268 9.50703V9.90703ZM5.39668 6.20703C5.39668 8.22315 7.20628 9.90703 9.50268 9.90703V9.50703C7.39147 9.50703 5.79668 7.96813 5.79668 6.20703H5.39668ZM4.79668 6.20703C4.79668 3.80612 6.93097 1.90703 9.50268 1.90703V1.50703C6.74853 1.50703 4.39668 3.5486 4.39668 6.20703H4.79668ZM8.61764 10.4305C6.45692 10.0526 4.79668 8.32631 4.79668 6.20703H4.39668C4.39668 8.55184 6.22906 10.4188 8.54872 10.8245L8.61764 10.4305ZM1.79668 18.0771C1.79668 14.3195 4.78348 11.2475 8.60509 10.8263L8.56127 10.4287C4.55779 10.8699 1.39668 14.0953 1.39668 18.0771H1.79668ZM2.09668 18.3771C1.93099 18.3771 1.79668 18.2428 1.79668 18.0771H1.39668C1.39668 18.4637 1.71008 18.7771 2.09668 18.7771V18.3771ZM16.9087 18.3771H2.09668V18.7771H16.9087V18.3771ZM17.2087 18.0771C17.2087 18.2428 17.0744 18.3771 16.9087 18.3771V18.7771C17.2953 18.7771 17.6087 18.4637 17.6087 18.0771H17.2087ZM10.4003 10.8263C14.2219 11.2475 17.2087 14.3195 17.2087 18.0771H17.6087C17.6087 14.0953 14.4476 10.8699 10.4441 10.4287L10.4003 10.8263ZM14.2087 6.20703C14.2087 8.32631 12.5484 10.0525 10.3877 10.4305L10.4566 10.8245C12.7763 10.4188 14.6087 8.55184 14.6087 6.20703H14.2087ZM9.50268 1.90703C12.0744 1.90703 14.2087 3.80612 14.2087 6.20703H14.6087C14.6087 3.5486 12.2568 1.50703 9.50268 1.50703V1.90703ZM16.5878 17.561C16.308 14.1147 13.2582 11.3771 9.50268 11.3771V11.7771C13.0667 11.7771 15.9275 14.3712 16.1891 17.5933L16.5878 17.561ZM2.61691 17.7771H16.3884V17.3771H2.61691V17.7771ZM9.50268 11.3771C5.74712 11.3771 2.69739 14.1147 2.41757 17.561L2.81625 17.5933C3.07789 14.3712 5.93866 11.7771 9.50268 11.7771V11.3771Z" fill="white" mask="url(#path-1-outside-1_1029_1560)"></path>
                            </g>
                            <defs>
                                <filter id="filter0_d_1029_1560" x="0.396484" y="0.507812" width="18.2119" height="19.2695" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                <feOffset></feOffset>
                                <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                <feComposite in2="hardAlpha" operator="out"></feComposite>
                                <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1560"></feBlend>
                                <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1560" result="shape"></feBlend>
                                </filter>
                            </defs>
                            </svg>
                        </span>
                        <span class="cart-icon ">
                            <svg xmlns="http://www.w3.org/2000/svg" width="21" height="20" viewBox="0 0 21 20" fill="none">
                            <g filter="url(#filter0_d_1029_1564)">
                                <mask id="path-1-outside-1_1029_1564" maskUnits="userSpaceOnUse" x="0.40918" y="0.707031" width="19" height="19" fill="black">
                                <rect fill="white" x="0.40918" y="0.707031" width="19" height="19"></rect>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M10.2048 1.70703C8.17708 1.70703 6.53442 3.35065 6.53442 5.3775V6.63916H1.90918C1.63304 6.63916 1.40918 6.86302 1.40918 7.13916V18.0772C1.40918 18.3534 1.63304 18.5772 1.90918 18.5772H18.5005C18.7766 18.5772 19.0005 18.3534 19.0005 18.0772V7.13916C19.0005 6.86302 18.7766 6.63916 18.5005 6.63916H13.8753V5.3775C13.8753 3.3505 12.231 1.70703 10.2048 1.70703ZM7.53442 5.3775C7.53442 3.90276 8.72954 2.70703 10.2048 2.70703C11.6789 2.70703 12.8753 3.90292 12.8753 5.3775V6.63885H7.53442V5.3775ZM2.40918 17.5772V7.63916H18.0005V17.5772H2.40918Z"></path>
                                </mask>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M10.2048 1.70703C8.17708 1.70703 6.53442 3.35065 6.53442 5.3775V6.63916H1.90918C1.63304 6.63916 1.40918 6.86302 1.40918 7.13916V18.0772C1.40918 18.3534 1.63304 18.5772 1.90918 18.5772H18.5005C18.7766 18.5772 19.0005 18.3534 19.0005 18.0772V7.13916C19.0005 6.86302 18.7766 6.63916 18.5005 6.63916H13.8753V5.3775C13.8753 3.3505 12.231 1.70703 10.2048 1.70703ZM7.53442 5.3775C7.53442 3.90276 8.72954 2.70703 10.2048 2.70703C11.6789 2.70703 12.8753 3.90292 12.8753 5.3775V6.63885H7.53442V5.3775ZM2.40918 17.5772V7.63916H18.0005V17.5772H2.40918Z" fill="white"></path>
                                <path d="M6.53442 6.63916V6.83916C6.64488 6.83916 6.73442 6.74962 6.73442 6.63916H6.53442ZM13.8753 6.63916H13.6753C13.6753 6.74962 13.7648 6.83916 13.8753 6.83916V6.63916ZM12.8753 6.63885V6.83885C12.9858 6.83885 13.0753 6.74931 13.0753 6.63885H12.8753ZM7.53442 6.63885H7.33442C7.33442 6.74931 7.42397 6.83885 7.53442 6.83885V6.63885ZM2.40918 7.63916V7.43916C2.29872 7.43916 2.20918 7.5287 2.20918 7.63916H2.40918ZM2.40918 17.5772H2.20918C2.20918 17.6877 2.29872 17.7772 2.40918 17.7772V17.5772ZM18.0005 7.63916H18.2005C18.2005 7.5287 18.1109 7.43916 18.0005 7.43916V7.63916ZM18.0005 17.5772V17.7772C18.1109 17.7772 18.2005 17.6877 18.2005 17.5772H18.0005ZM6.73442 5.3775C6.73442 3.46107 8.28757 1.90703 10.2048 1.90703V1.50703C8.06658 1.50703 6.33442 3.24023 6.33442 5.3775H6.73442ZM6.73442 6.63916V5.3775H6.33442V6.63916H6.73442ZM1.90918 6.83916H6.53442V6.43916H1.90918V6.83916ZM1.60918 7.13916C1.60918 6.97347 1.74349 6.83916 1.90918 6.83916V6.43916C1.52258 6.43916 1.20918 6.75256 1.20918 7.13916H1.60918ZM1.60918 18.0772V7.13916H1.20918V18.0772H1.60918ZM1.90918 18.3772C1.74349 18.3772 1.60918 18.2429 1.60918 18.0772H1.20918C1.20918 18.4638 1.52258 18.7772 1.90918 18.7772V18.3772ZM18.5005 18.3772H1.90918V18.7772H18.5005V18.3772ZM18.8004 18.0772C18.8004 18.2429 18.6661 18.3772 18.5005 18.3772V18.7772C18.887 18.7772 19.2005 18.4638 19.2005 18.0772H18.8004ZM18.8004 7.13916V18.0772H19.2005V7.13916H18.8004ZM18.5005 6.83916C18.6661 6.83916 18.8004 6.97347 18.8004 7.13916H19.2005C19.2005 6.75256 18.887 6.43916 18.5005 6.43916V6.83916ZM13.8753 6.83916H18.5005V6.43916H13.8753V6.83916ZM13.6753 5.3775V6.63916H14.0753V5.3775H13.6753ZM10.2048 1.90703C12.1206 1.90703 13.6753 3.46098 13.6753 5.3775H14.0753C14.0753 3.24001 12.3415 1.50703 10.2048 1.50703V1.90703ZM10.2048 2.50703C8.61905 2.50703 7.33442 3.79234 7.33442 5.3775H7.73442C7.73442 4.01319 8.84003 2.90703 10.2048 2.90703V2.50703ZM13.0753 5.3775C13.0753 3.79244 11.7893 2.50703 10.2048 2.50703V2.90703C11.5685 2.90703 12.6753 4.0134 12.6753 5.3775H13.0753ZM13.0753 6.63885V5.3775H12.6753V6.63885H13.0753ZM7.53442 6.83885H12.8753V6.43886H7.53442V6.83885ZM7.33442 5.3775V6.63885H7.73442V5.3775H7.33442ZM2.20918 7.63916V17.5772H2.60918V7.63916H2.20918ZM18.0005 7.43916H2.40918V7.83916H18.0005V7.43916ZM18.2005 17.5772V7.63916H17.8004V17.5772H18.2005ZM2.40918 17.7772H18.0005V17.3772H2.40918V17.7772Z" fill="white" mask="url(#path-1-outside-1_1029_1564)"></path>
                            </g>
                            <defs>
                                <filter id="filter0_d_1029_1564" x="0.208984" y="0.507812" width="19.9912" height="19.2695" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
                                <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
                                <feOffset></feOffset>
                                <feGaussianBlur stdDeviation="0.5"></feGaussianBlur>
                                <feComposite in2="hardAlpha" operator="out"></feComposite>
                                <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"></feColorMatrix>
                                <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_1029_1564"></feBlend>
                                <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_1029_1564" result="shape"></feBlend>
                                </filter>
                            </defs>
                            </svg>
                        </span>
                    </div>

                </div>
            </section>
        </div>
        <!-- Header element ends -->

    </header>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'HeaderBar',
    emits: ['enable-search-bar'],
    methods: {
        reloadPage(){
            window.location.reload();
        }
    }
})
</script>

<style scoped>
.hide {
    display: none;
}
.Header-Wrapper {
    width: 100%;
}

.logo a svg{
    height: 20px;
}

.menu-wrapper-top {
    display: flex;
    padding-top: 20px;
    padding-bottom: 20px;
    margin: 0px 20px;
}

.header-logo {
    margin-left: 30px;
}

.burger-icon svg, .search-icon svg path, .cart-icon svg path, .profile-icon svg path{
    fill: #2f343e;
    filter: none;
}

@media (max-width: 480px) {
    .right-side-icon {
        gap: 25px;
    }
}
</style>
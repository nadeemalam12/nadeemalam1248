# Ginger Hotels     //  (   https://www.gingerhotels.com/  )

#HomePage.jsx

import React, { useState, useEffect } from "react";
import { ChevronLeft, ChevronRight, MapPin } from "lucide-react"; // npm install lucide-react
import { Wifi, Car, Coffee, Dumbbell } from "lucide-react";

import { FaMagnifyingGlass } from "react-icons/fa6";
import { FaChevronDown, FaBars, FaTimes } from 'react-icons/fa';

import { Helmet } from "react-helmet";

const Home = () => {
    // Slider
    const heroImages = [
        'https://images.unsplash.com/photo-1566073771259-6a8506099945?w=1200&h=600&fit=crop',
        'https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?w=1200&h=600&fit=crop',
        'https://images.unsplash.com/photo-1571896349842-33c89424de2d?w=1200&h=600&fit=crop',
        'https://www.travelandleisure.com/thmb/JIoqZXurmgjBU-aRjKthU7oKu8A=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/1-71d7208a004a48b7bc1617a7e77183ea.jpg',
        'https://seaviewmaltahotel.com/wp-content/uploads/2022/11/Sewview-Hotel-Bugibba-1310-min.jpg'
    ];

    const [currentSlide, setCurrentSlide] = useState(0);
    const [checkIn, setCheckIn] = useState("");
    const [checkOut, setCheckOut] = useState("");
    const [guests, setGuests] = useState(1);

    const nextSlide = () => {
        setCurrentSlide((prev) => (prev + 1) % heroImages.length);
    };

    const prevSlide = () => {
        setCurrentSlide((prev) => (prev - 1 + heroImages.length) % heroImages.length);
    };

    useEffect(() => {
        const interval = setInterval(nextSlide, 5000);
        return () => clearInterval(interval);
    }, []);



    return (
        <>


            {/* Slider Section */}
            <section id="home" className="relative h-screen overflow-hidden">
                <div className="absolute inset-0">
                    {heroImages.map((image, index) => (
                        <div
                            key={index}
                            className={`absolute inset-0 transition-opacity duration-1000 ${index === currentSlide ? "opacity-100" : "opacity-0"
                                }`}
                        >
                            <img
                                src={image}
                                alt={`Hotel view ${index + 1}`}
                                className="w-full h-full object-cover"
                            />
                        </div>
                    ))}
                </div>
   
                <div className="absolute inset-0 bg-black/40" />

                <button
                    onClick={prevSlide}
                    className="absolute left-4 top-1/2 transform -translate-y-1/2 text-white/80 hover:text-white transition-colors z-10"
                >
                    <ChevronLeft size={40} />
                </button>

                <button
                    onClick={nextSlide}
                    className="absolute right-4 top-1/2 transform -translate-y-1/2 text-white/80 hover:text-white transition-colors z-10"
                >
                    <ChevronRight size={40} />
                </button>

                <div className="relative z-10 flex items-center justify-center h-full">
                    <div className="text-center text-white max-w-4xl mx-auto px-4">
                        <h2 className="text-5xl md:text-7xl font-bold mb-6 animate-fade-in pacifico-font">
                            Welcome to <span className="text-[#FFA100] pacifico-font">LuxeStay</span>
                        </h2>
                        <p className="text-xl md:text-2xl mb-8 text-gray-200">
                            Experience luxury redefined in the heart of paradise
                        </p>
                        <div className="flex items-center justify-center space-x-2 mb-8">
                            <MapPin className="text-[#FFA100]" size={20} />
                            <span className="text-lg">Downtown Miami, Florida</span>
                        </div>
                    <a href="/bookingform"><button className="bg-[#FFA100] hover:bg-orange-400 text-white px-8 py-4 rounded-full text-lg font-semibold transition-all transform hover:scale-105 shadow-lg">
                            Book Your Stay
                        </button></a>
                    </div>
                </div>

                <div className="absolute bottom-8 left-1/2 transform -translate-x-1/2 flex space-x-2 z-10">
                    {heroImages.map((_, index) => (
                        <button
                            key={index}
                            onClick={() => setCurrentSlide(index)}
                            className={`w-3 h-3 rounded-full transition-colors ${index === currentSlide ? "bg-white" : "bg-white/50"
                                }`}
                        />
                    ))}
                </div>
            </section>

            {/* Booking Section */}
            <section className="py-16 to-indigo-50">
                <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                    <div className="bg-white rounded-2xl shadow-xl p-8">
                        <h3 className="text-2xl font-bold text-center mb-8 text-gray-900 pacifico-font">Book Your Perfect Stay</h3>
                        <div className="grid grid-cols-1 md:grid-cols-4 gap-6">
                            <div>
                                <label className="block text-sm font-medium text-gray-700 mb-2">Check-in Date</label>
                                <input
                                    type="date"
                                    value={checkIn}
                                    onChange={(e) => setCheckIn(e.target.value)}
                                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                                />
                            </div>
                            <div>
                                <label className="block text-sm font-medium text-gray-700 mb-2">Check-out Date</label>
                                <input
                                    type="date"
                                    value={checkOut}
                                    onChange={(e) => setCheckOut(e.target.value)}
                                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                                />
                            </div>
                            <div>
                                <label className="block text-sm font-medium text-gray-700 mb-2">Guests</label>
                                <select
                                    value={guests}
                                    onChange={(e) => setGuests(Number(e.target.value))}
                                    className="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                                >
                                    <option value={1}>1 Guest</option>
                                    <option value={2}>2 Guests</option>
                                    <option value={3}>3 Guests</option>
                                    <option value={4}>4 Guests</option>
                                </select>
                            </div>
                            <div className="flex items-end">
                                <button className="w-full bg-[#FFA100] hover:bg-orange-400 text-white py-3 px-6 rounded-lg font-semibold transition-colors">
                                    Search Rooms
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            {/* Home Section 2 */}
            <div className="h-[90vh] w-full text-center flex flex-col items-center justify-center px-4">
                <img
                    src="/img/sectionImg.png"
                    alt="Hotel experience"
                    className="h-[30vh] sm:h-[40vh] md:h-[50vh] object-cover rounded-lg"
                />
                <p className="mt-0 sm:mt-10 md:mt-12 text-sm sm:text-base md:text-lg lg:text-xl text-gray-700 max-w-2xl mx-auto px-4">
                    Getting the best of both worlds is simply better, isn't it?
                </p>

                <button className="-mt-50 rounded-full border-none px-6 py-3 sm:px-8 sm:py-4 bg-pink-600 hover:bg-pink-700 mt-8 sm:mt-12 md:mt-16 text-white font-medium transition-colors duration-300 transform hover:scale-105">
                    Explore
                </button>
            </div>



{/* vedio section */}

<div className="min-h-screen w-full flex flex-col md:flex-row justify-center md:justify-around items-center gap-16 sm:gap-20 md:gap-4 lg:gap-6 xl:gap-8 px-3 sm:px-4 md:px-6 lg:px-8 py-8 sm:py-12 md:py-0">

    {/* Video 1 - Stagger Up */}
    <div className="flex flex-col items-center stagger-up w-full max-w-xs sm:max-w-none">
        <video
            className="-mt-4 sm:-mt-8 md:-mt-[25vh] lg:-mt-[25vh] xl:-mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/sample.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#F53F1B] text-center px-2">
            Lean Luxe
        </h4>
    </div>

    {/* Video 2 - Stagger Down */}
    <div className="flex flex-col items-center stagger-down w-full max-w-xs sm:max-w-none">
        <video
            className="mt-4 sm:mt-8 md:mt-[25vh] lg:mt-[25vh] xl:mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/hotel.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#FFA100] text-center px-2">
            Vibrant Spaces
        </h4>
    </div>

    {/* Video 3 - Stagger Up */}
    <div className="flex flex-col items-center stagger-up w-full max-w-xs sm:max-w-none">
        <video
            className="-mt-4 sm:-mt-8 md:-mt-[25vh] lg:-mt-[25vh] xl:-mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/sample.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#E11162] text-center px-2">
            Qmin - All Day Dining
        </h4>
    </div>

    {/* Video 4 - Stagger Down */}
    <div className="flex flex-col items-center stagger-down w-full max-w-xs sm:max-w-none">
        <video
            className="mt-4 sm:mt-8 md:mt-[25vh] lg:mt-[25vh] xl:mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/hotel.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#F53F1B] text-center px-2">
            Intuitive and High Energy
        </h4>
    </div>

    {/* Video 5 - Stagger Up */}
    <div className="flex flex-col items-center stagger-up w-full max-w-xs sm:max-w-none">
        <video
            className="-mt-4 sm:-mt-8 md:-mt-[25vh] lg:-mt-[25vh] xl:-mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/sample.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#FFA100] text-center px-2">
            Thoughtful Amenities
        </h4>
    </div>

    {/* Video 6 - Stagger Down */}
    <div className="flex flex-col items-center stagger-down w-full max-w-xs sm:max-w-none">
        <video
            className="mt-4 sm:mt-8 md:mt-[25vh] lg:mt-[25vh] xl:mt-[25vh] w-28 h-36 xs:w-32 xs:h-40 sm:w-36 sm:h-44 md:w-40 md:h-48 lg:w-44 lg:h-56 xl:w-52 xl:h-64 object-cover rounded-2xl sm:rounded-3xl shadow-lg"
            autoPlay
            loop
            muted
            playsInline
        >
            <source src="/img/hotel.mp4" type="video/mp4" />
            Your browser does not support the video tag.
        </video>
        <h4 className="mt-3 sm:mt-4 text-xs sm:text-sm md:text-base lg:text-lg font-semibold text-[#E11162] text-center px-2">
            Convenient Locations
        </h4>
    </div>

</div>



            {/* /// */}

            <section
                id="amenities"
                className="py-20 bg-cover bg-center bg-no-repeat"
                style={{ backgroundImage: "url('/img/line5.webp')" }}
            >
                <div className="bg-white/80 backdrop-blur-sm py-12">
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div className="text-center mb-16">
                            <h2 className="text-4xl font-bold text-gray-900 mb-4 pacifico-font">
                                World-Class Amenities
                            </h2>
                            <p className="text-xl text-gray-600 max-w-2xl mx-auto">
                                Indulge in our premium facilities designed for your comfort and convenience
                            </p>
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                            {[
                                { icon: Wifi, title: 'Free WiFi', desc: 'High-speed internet throughout the hotel' },
                                { icon: Car, title: 'Valet Parking', desc: '24/7 secure parking service service service' },
                                { icon: Coffee, title: 'Restaurant & Bar', desc: 'Fine dining and craft cocktails equipment' },
                                { icon: Dumbbell, title: 'Fitness Center', desc: 'State-of-the-art equipment equipment' },
                            ].map((amenity, index) => (
                                <div key={index} className="text-center group">
                                    <div className="bg-white rounded-2xl p-8 shadow-lg hover:shadow-xl transition-shadow">
                                        <div className="inline-flex items-center justify-center w-16 h-16 bg-[#FFA100] rounded-full mb-4 group-hover:bg-[#E11162] transition-colors">
                                            <amenity.icon className="text-[#00000]" size={32} />
                                        </div>
                                        <h3 className="text-xl font-semibold text-gray-900 mb-2">{amenity.title}</h3>
                                        <p className="text-gray-600">{amenity.desc}</p>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </div>
            </section>


        </>
    );
};

export default Home;



// * for slider i need to install this liabery = npm install lucide-react
// * npm install react-helmet
// * for adding font style = <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet" /> , src => style.css => .pacifico-font {
//   font-family: 'Pacifico', cursive;
// }


#AboutUS.jsx    // page_flie

import React from "react";
import { Swiper, SwiperSlide } from 'swiper/react';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

import crousel1 from '../aboutimg/crousel1.jpg';
import crousel2 from '../aboutimg/crousel2.jpg';
import crousel3 from '../aboutimg/crousel3.jpg';
import crousel4 from '../aboutimg/crousel4.jpg';
import crousel5 from '../aboutimg/crousel5.jpg';
// Hotel images
import image1 from "../Images/image1.png"
import image3 from "../Images/image3.png"
import image4 from "../Images/image4.png"
import image5 from "../Images/image5.png"
import Container1 from "../Images/Container1.png"
import Container2 from "../Images/Container2.png"
import Container3 from "../Images/Container3.png"
import Container4 from "../Images/Container4.png"


// offers
import img1 from "../Images/img1.png"
import img2 from "../Images/img2.png"
import img3 from "../Images/img3.png"
import holeimg from "../Images/holeimg.png"
import employee1 from "../Images/employee1.png"
import employee3 from "../Images/employee3.png"
import employee4 from "../Images/employee4.jpg"



const AboutUs = () => {
    return (
        <>
            <div className="w-full min-h-screen  py-10">
                <h1 className="text-4xl md:text-5xl font-bold ml-30 mb-10">About Us</h1>

                <div className="w-[90%] max-w-12xl mx-auto">
                    <Swiper
                        modules={[Navigation, Pagination, Autoplay]}
                        spaceBetween={30}
                        slidesPerView={1}
                        navigation
                        pagination={{ clickable: true }}
                        autoplay={{ delay: 3000 }}
                        loop
                        className="rounded-2xl overflow-hidden"
                    >
                        {[crousel1, crousel2, crousel3, crousel4, crousel5].map((image, index) => (
                            <SwiperSlide key={index}>
                                <img src={image} alt={`crousel${index + 1}`} className="w-full h-[300px] md:h-[500px] object-cover" />
                            </SwiperSlide>
                        ))}
                    </Swiper>
                </div>
            </div>

            <div className="w-full h-[40rem] bg-white">
                <h1 className="text-center italic text-6xl">Featured Ginger Hotels</h1>

                <div className="w-full h-[28rem] bg-blue-50  flex gap-4 rounded-2xl mt-13">
                    <div className="w-[24%] h-[28rem] bg-white shadow-2xl rounded-2xl">
                        <div className="w-full h-[12rem] bg-white rounded-2xl ">
                            <img className="w-full h-[12rem]" src={image1} alt="image1" />
                        </div>
                        <div className="w-[95%] h-[12rem] bg-white ml-[2.5%]">
                            <img className="w-full h-[12rem] " src={Container1} alt="Container1" />
                        </div>
                        <div className="w-full h-[3.2rem] bg-white flex gap-5 ">
                            <p className="ml-3 text-orange-700 underline ">View Hotel</p>
                            <button className="w-[49%] h-[2.5rem] bg-orange-400 rounded-full ... tect-xl  font-bold text-white hover:bg-red-600" >Book Your Stay</button>
                        </div>

                    </div>
                    <div className="w-[24%] h-[28rem] bg-white rounded-2xl shadow-2xl">
                        <div className="w-full h-[12rem] bg-white rounded-2xl">
                            <img className="w-full h-[12rem]" src={image3} alt="image3" />
                        </div>
                        <div className="w-[95%] h-[12rem] bg-white ml-[2.5%]">
                            {/* <p className="w-[98%] h-[2rem] bg-blue-400 text-xl font-bold">Ginger Diu, Jalandhar Beach</p> */}
                            <img className="w-full h-[12rem] " src={Container2} alt="Container3" />

                        </div>
                        <div className="w-full h-[3.2rem] bg-white flex gap-5 ">
                            <p className="ml-3 text-orange-700 underline ">View Hotel</p>
                            <button className="w-[49%] h-[2.5rem] bg-orange-400 rounded-full ... tect-xl  font-bold text-white hover:bg-orange-600" >Book Your Stay</button>
                        </div>
                    </div>

                    <div className="w-[24%] h-[28rem] bg-white rounded-2xl shadow-2xl">
                        <div className="w-full h-[12rem] bg-white rounded-2xl">
                            <img className="w-full h-[12rem]" src={image4} alt="image4" />
                        </div>
                        <div className="w-[95%] h-[12rem] bg-white ml-[2.5%]">
                            {/* <p className="w-[95%] h-[2rem] bg-blue-400 text-xl font-bold">Ginger Mumbai, Airport</p> */}
                            <img className="w-full h-[12rem] " src={Container3} alt="Container3" />

                        </div>
                        <div className="w-full h-[3.2rem] bg-white flex gap-5 ">
                            <p className="ml-3 text-orange-700 underline">View Hotel</p>
                            <button className="w-[49%] h-[2.5rem] bg-orange-400 rounded-full ... tect-xl  font-bold text-white hover:bg-orange-600" >Book Your Stay</button>
                        </div>
                    </div>

                    <div className="w-[24%] h-[28rem] bg-white rounded-2xl shadow-2xl">
                        <div className="w-full h-[12rem] bg-white rounded-2xl">
                            <img className="w-full h-[12rem]" src={image5} alt="image5" />
                        </div>
                        <div className="w-[95%] h-[12rem] bg-white ml-[2.5%]">
                            {/* <p className="w-[95%] h-[2rem] bg-blue-400 text-xl font-bold">Ginger Goa, Candolim</p> */}
                            <img className="w-full h-[12rem] " src={Container4} alt="Container4" />

                        </div>
                        <div className="w-full h-[3.2rem] bg-white flex gap-5 ">
                            <p className="ml-3 text-orange-700 underline ">View Hotel</p>
                            <button className="w-[49%] h-[2.5rem] bg-orange-400 rounded-full ... text-xl  font-bold text-white hover:bg-orange-600" >Book Your Stay</button>
                        </div>
                    </div>
                </div>
            </div>


            <div className="w-full h-[36rem] bg-white">
                <div className="w-full h-[6rem] bg-white">
                    <h1 className="text-6xl text-center font-bold italic">Offers</h1>
                </div>

                <div className="w-full h-[25rem] bg-white ">
                    <div className="w-[75%] h-[25rem]  ml-[12%] flex gap-2" >
                        <div className="w-[34%] h-[25rem] bg-white rounded-2xl shadow-2xl">
                            <div className="w-full h-[11rem] bg-white rounded-2xl ">
                                <img className="w-full h-[11rem]" src={img1} alt="img1" />
                            </div>
                            <p className="w-[80%] h-10 bg-white text-xl font-bold ml-3 ">Cherishing Togetherness</p>
                            <p className="w-full h-20 bg-white text-sm text-center">This cricket season, enjoy 25% savings on breakfast-
                                inclusive stays and more as our valued NeuPass members....</p>
                            <div className="w-[38%] h-10 rounded-2xl bg-orange-500 ml-3 mt-4 text-center hover:bg-red-600">
                                <button className="w-[35%] h-10  rounded-2xl">Login/join</button>
                            </div>
                            <p className="text-orange-700 ml-40 text-xl fond-bold ">Know More</p>
                        </div>

                        <div className="w-[34%] h-[25rem] bg-white rounded-2xl shadow-2xl">
                            <div className="w-full h-[11rem] bg-white rounded-2xl ">
                                <img className="w-full h-[11rem]" src={img2} alt="img2" />
                            </div>
                            <p className="w-[80%] h-10 bg-white text-xl font-bold ml-3 ">Breakfast Inclusive Rate</p>
                            <p className="w-full h-20 bg-white text-sm text-center">Wake up to a symphony of flavours with our delectable
                                breakfast spread and enjoy seamless internet
                                connectivity and flexible cancellation for that add...</p>
                            <div className="w-[38%] h-10 rounded-2xl bg-orange-500 ml-3 mt-4 text-center hover:bg-orange-800">
                                <button className="w-[35%] h-10  rounded-2xl  ">Login/join</button>
                            </div>
                            <p className="text-orange-700 ml-40 text-xl fond-bold underline">Know More</p>

                        </div>

                        <div className="w-[34%] h-[25rem] bg-white rounded-2xl shadow-2xl">
                            <div className="w-full h-[11rem] bg-white rounded-2xl ">
                                <img className="w-full h-[11rem]" src={img3} alt="img3" />
                            </div>
                            <p className="w-[80%] h-10 bg-white text-xl font-bold ml-3 ">New Beginnings</p>
                            <p className="w-full h-20 bg-white text-sm text-center">Indulge the explorer in you and set out to discover our
                                newest hotels and novel experiences. Enjoy exclusive
                                25% savings on breakfast-inclusive rates ...</p>
                            <div className="w-[38%] h-10 rounded-2xl bg-orange-500 ml-3 mt-4 text-center hover:bg-pink-800">
                                <button className="w-[35%] h-10  rounded-2xl ">Login/join</button>
                            </div>
                            <p className="text-orange-700 ml-40 text-xl fond-bold underline">Know More</p>

                        </div>

                    </div>
                </div>
            </div>

            <div className="w-[95%] h-[30rem] bg-white ml-[2.5%] mt-10">
                <h1 className="text-5xl text-center font-bold italic">Meet. Connect. Be Social</h1>
                <div className="w-[90%] h-[22rem] bg-white ml-[5%] mt-3 flex gap-10">
                    <div className="w-[65%] h-[20rem] bg-white ml-5 rounded-2xl mt-3  ">
                        <img className="w-full h-[20rem] " src={holeimg} alt="holeimg" />
                    </div>
                    <div className="w-[40%] h-[20rem] bg-white mt-3 rounded-xl">
                        <div className="w-35 h-15 mt-5 ml-3 bg-white"><h1 className="italic">Qmin</h1></div>
                        <div className="w-full h-[9rem]"><p className="italic">Looking for a delightful escape from the bustling city? Step into Qmin at
                            Ginger Hotels and immerse yourself in a world of vibrant flavours,
                            refreshing beverages, and big-screen thrills. Discover a colourful setting
                            where you can relish delicious food and create joyful memories with your
                            favourite people.</p></div><br></br>
                        <div className="w-34 h-11 bg-orange-400 ml-4 rounded-2xl">
                            <button className="text-center w-full h-11">Feel the buzz</button>
                        </div>
                    </div>
                </div>
            </div>



            <div className="w-full h-[53rem] bg-blue-400">
                <div className="w-[50%] h-[52rem] bg-pink-500">
                    <div className="w-full h-[17rem] bg-blue-200 flex flex-nowrap ">
                        <div className="w-[35%] h-[17rem] bg-yellow-400">
                            <div className="w-full h-[17rem] bg-pink-600">
                                <img className="h-full" src={employee1} alt="employee1" />
                            </div>
                        </div>

                        <div className="w-[65%] h-[17rem]">
                            <h1 className="text-3xl ml-35 text-bolt">AYESHA KHAN </h1><br></br>
                            <p className="text-xl ml-5 "> About AYESHA KHAN
                                AYESHA KHAN is a director registered with Ministry of Corporate Affairs.
                                Their Director Identification Number (DIN) is 08556908.
                                AYESHA KHAN is/has been associated with 2 companies.</p>
                        </div>

                    </div>

                    <div className="w-full h-[17rem] bg-blue-200 flex flex-nowrap ">
                        <div className="w-[35%] h-[17rem] bg-yellow-400">
                            <div className="w-full h-[17rem] bg-pink-600">
                                <img className="h-full" src={employee3} alt="employee3" />
                            </div>
                        </div>

                        <div className="w-[65%] h-[17rem]">
                            <h1 className="text-3xl ml-35 text-bolt">Md Ayyub KHAN </h1><br></br>
                            <p className="text-xl ml-5 "> About AYESHA KHAN
                                AYESHA KHAN is a director registered with Ministry of Corporate Affairs.
                                Their Director Identification Number (DIN) is 08556908.
                                AYESHA KHAN is/has been associated with 2 companies.</p>
                        </div>

                    </div>

                    <div className="w-full h-[17rem] bg-blue-200 flex flex-nowrap ">
                        <div className="w-[35%] h-[17rem] bg-yellow-400">
                            <div className="w-full h-[17rem] bg-pink-600">
                                <img className="h-full" src={employee4} alt="employee4" />
                            </div>
                        </div>

                        <div className="w-[65%] h-[17rem]">
                            <h1 className="text-3xl ml-35 text-bolt">Md Aarib f </h1><br></br>
                            <p className="text-xl ml-5 "> About AYESHA KHAN
                                AYESHA KHAN is a director registered with Ministry of Corporate Affairs.
                                Their Dir ector Identification Number (DIN) is 08556908.
                                AYESHA KHAN is/has been associated with 2 companies.</p>
                        </div>

                    </div>

                </div>

                <div className="w-[50%] h-[20rem] bg-pink-300"></div>

            </div>
        </>
    );
};

export default AboutUs;



#Footer.jsx   Pagefile 

import React from "react";


const Footer = () => {

    
    const handleIconClick = (e) => {
        e.currentTarget.style.transform = "scale(0.95)";
        setTimeout(() => {
            e.currentTarget.style.transform = "scale(1)";
        }, 150);
    };

    const handleMouseEnter = (e) => {
        e.currentTarget.style.transform = "translateX(4px)";
    };

    const handleMouseLeave = (e) => {
        e.currentTarget.style.transform = "translateX(0)";
    };

    return(
        <>
        
         {/* footer*/}
            {/* <div className="h-0.5 bg-gradient-to-r from-[#FFA100] via-[#E11162] to-[#E11162]"></div> */}
            <footer className="bg-[white]">
                {/* Logo Section */}
                <div className="px-4 sm:px-6 lg:px-8 pt-8 pb-4">
                    <div className="max-w-7xl mx-auto">
                        <div className="flex items-center">
                            <div className="w-32 h-16 bg-gray-300 rounded flex items-center justify-center">
                                <span className="text-sm font-semibold text-gray-600">HOTEL LOGO</span>
                            </div>
                        </div>
                    </div>
                </div>

                {/* Main Footer Content */}
                <div className="px-4 sm:px-6 lg:px-8 pb-8">
                    <div className="max-w-7xl mx-auto">
                        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 lg:gap-6">
                            {/* Social Media & Contact Section */}
                            <div className="lg:col-span-1 space-y-6">
                                <div>
                                    <h2 className="text-lg font-semibold text-gray-800 mb-4 pacifico-font">FOLLOW US ON</h2>
                                    <div className="flex space-x-3">
                                        {/* Social Icons */}
                                        {[
                                            { color: "bg-blue-600", hover: "hover:bg-blue-700" },
                                            { color: "bg-blue-800", hover: "hover:bg-blue-900" },
                                            { color: "bg-pink-600", hover: "hover:bg-pink-700" },
                                            { color: "bg-red-600", hover: "hover:bg-red-700" },
                                        ].map((style, i) => (
                                            <div
                                                key={i}
                                                className={`w-10 h-10 ${style.color} ${style.hover} rounded-full flex items-center justify-center transition-colors cursor-pointer`}
                                                onClick={handleIconClick}
                                            >
                                                <svg className="w-5 h-5 text-white" fill="currentColor" viewBox="0 0 24 24">
                                                    <path d="M12 0C5.372 0 0 5.373 0 12s5.372 12 12 12 12-5.373 12-12S18.628 0 12 0z" />
                                                </svg>
                                            </div>
                                        ))}
                                    </div>
                                </div>

                                {/* Contact Section */}
                                <div>
                                    <h2 className="text-lg font-semibold text-gray-800 mb-4 pacifico-font">CONTACT US</h2>
                                    <div className="space-y-2">
                                        <p className="text-gray-700">
                                            <strong className="font-semibold">CALL:</strong>{" "}
                                            <a
                                                href="tel:8700898990"
                                                className="hover:text-blue-600 transition-colors"
                                                onMouseEnter={handleMouseEnter}
                                                onMouseLeave={handleMouseLeave}
                                            >
                                                8700898990
                                            </a>
                                        </p>
                                        <p className="text-gray-700">
                                            <strong className="font-semibold">EMAIL:</strong>{" "}
                                            <a
                                                href="mailto:ssourabh.1712@gmail.com"
                                                className="hover:text-blue-600 transition-colors break-all"
                                                onMouseEnter={handleMouseEnter}
                                                onMouseLeave={handleMouseLeave}
                                            >
                                                ssourabh.1712@gmail.com
                                            </a>
                                        </p>
                                    </div>
                                </div>
                            </div>

                            {/* Quick Links Repeated Sections */}
                            {[1, 2, 3].map((section, i) => (
                                <div key={i} className="space-y-4">
                                    <h3
                                        className={`text-lg font-semibold text-gray-800 pacifico-font ${i === 0 ? "" : "invisible"
                                            }`}
                                    >
                                        {i === 0 ? "Quick Links" : "Links"}
                                    </h3>
                                    <ul className="space-y-2">
                                        {[
                                            "Hotel",
                                            "Offer",
                                            "Neupass",
                                            "Business Connect",
                                            "Blog",
                                            "Sitemap",
                                            "About Ginger",
                                            "Careers",
                                        ].map((link, idx) => (
                                            <li key={idx}>
                                                <a
                                                    href="#"
                                                    className="text-black-600 hover:text-black-800 transition-colors"
                                                    onMouseEnter={handleMouseEnter}
                                                    onMouseLeave={handleMouseLeave}
                                                >
                                                    {link}
                                                </a>
                                            </li>
                                        ))}
                                    </ul>
                                </div>
                            ))}
                        </div>
                    </div>
                </div>

                {/* Gradient Divider */}
                <div className="h-0.5 bg-gradient-to-r from-[#FFA100] via-[#E11162] to-[#E11162]"></div>

                {/* Copyright */}
                <div className="bg-footerPink text-center py-4">
                    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <h4 className="text-black font-medium">Copyright © & About Krayons | 2014 - 24</h4>
                    </div>
                </div>
            </footer>

        </>
    )
}

export default Footer;


# Header.jsx     // page_File

import React, { useState } from "react";
import { FaMagnifyingGlass } from "react-icons/fa6";
import { FaChevronDown, FaBars, FaTimes } from 'react-icons/fa';

const Header = () => {
  const [menuOpen, setMenuOpen] = useState(false);
  const [moreOpen, setMoreOpen] = useState(false);

  return (
    <>
      {/* Main Navbar Container */}
      <div className="h-[80px] w-full flex items-center justify-between px-4 shadow-md">
        {/* Logo */}
        <div className="w-[15%] flex items-center pl-4">
        <a href="/"><img src="/img/Logo.svg" alt="Logo" className="w-[8.54vw] h-[2.86vw]" /></a>
        </div>

        {/* Center Menu */}
        <div className="hidden lg:flex h-[80px] w-[60%] items-center justify-center gap-[30px] text-[13px] font-medium">
         <a href="/"><li className="list-none cursor-pointer">Home</li></a>
         <a href="/about"><li className="list-none cursor-pointer">About us</li></a>
          <li className="list-none cursor-pointer">Restaurant</li>
          <li className="list-none cursor-pointer">Service</li>
          <li className="list-none cursor-pointer">Offer</li>
          <li className="list-none cursor-pointer">Eat</li>
          <li className="list-none cursor-pointer">Party</li>

          {/* Dropdown */}
          <li
            className="list-none flex items-center cursor-pointer relative"
            onClick={() => setMoreOpen(!moreOpen)}
          >
            More <FaChevronDown className="ml-[5px] mt-[2px]" />
            {moreOpen && (
              <ul className="absolute top-[40px] left-0 w-[200px] bg-white shadow-lg rounded-md text-black z-50">
                <li className="px-4 py-2 hover:bg-gray-100 cursor-pointer">Manage Your Bookings</li>
                <li className="px-4 py-2 hover:bg-gray-100 cursor-pointer">Contact Us</li>
              </ul>
            )}
          </li>
        </div>

        {/* Right Side */}
        <div className="hidden lg:flex h-[80px] w-[25%] items-center justify-end pr-4 text-[13px] font-medium space-x-4">
          <FaMagnifyingGlass className="text-[17px]" />
          <p>Login</p>
          <p>/</p>
          <a href="/login"><p>Admin</p></a>
          <a href="/bookingform"><button className="rounded-[30px] px-[20px] py-[10px] bg-orange-500 text-white">
            Book your stay
          </button></a>
        </div>

        {/* Hamburger Menu Button */}
        <div className="lg:hidden">
          <button onClick={() => setMenuOpen(!menuOpen)}>
            {menuOpen ? <FaTimes size={20} /> : <FaBars size={20} />}
          </button>
        </div>
      </div>

      {/* Mobile Menu */}
      {menuOpen && (
        <div className="lg:hidden px-4 py-3 bg-white shadow-md text-sm font-medium space-y-2">
          <ul className="space-y-2">
            <li className="cursor-pointer">Home</li>
            <li className="cursor-pointer">About us</li>
            <li className="cursor-pointer">Restaurant</li>
            <li className="cursor-pointer">Service</li>
            <li className="cursor-pointer">Offer</li>
            <li className="cursor-pointer">Eat</li>
            <li className="cursor-pointer">Party</li>
            <li>
              <button onClick={() => setMoreOpen(!moreOpen)} className="flex items-center gap-1">
                More <FaChevronDown />
              </button>
              {moreOpen && (
                <ul className="ml-4 mt-1 space-y-1 text-gray-700">
                  <li className="cursor-pointer">Manage Your Bookings</li>
                  <li className="cursor-pointer">Contact Us</li>
                </ul>
              )}
            </li>
          </ul>

          <div className="flex items-center gap-2 border-t pt-2">
            <FaMagnifyingGlass className="text-[17px]" />
            <span>Login / Logout</span>
          </div>
          <button className="w-full mt-2 rounded-[30px] px-4 py-2 bg-orange-500 text-white">
            Book your stay
          </button>
        </div>
      )}
    </>
  );
};

export default Header;

#Login.jsx    // page_File

import React, { useState } from 'react';
import axios from 'axios';
import { useNavigate } from 'react-router-dom';

const LoginForm = () => {
    const navigate = useNavigate();
    const [formData, setFormData] = useState({
        email: '',
        password: '',
        rememberMe: false
    });

    const handleInputChange = (e) => {
        const { id, value, type, checked } = e.target;
        setFormData({ ...formData, [id]: type === 'checkbox' ? checked : value });
    };

    const apiUrl = import.meta.env.VITE_API_URL || 'http://localhost:3000';

    const submitData = async (e) => {
        e.preventDefault();

        try {
            const response = await axios.post(`${apiUrl}/user/login`, {
                email: formData.email,
                password: formData.password
            });

            if (response.status === 200) {
                alert('User logged in successfully!');

                // Store user data properly based on your backend response structure
                const userData = {
                    email: response.data.email,
                    name: response.data.name, // This comes from your backend
                    userName: response.data.name, // Fallback if needed
                    token: response.data.jwtToken,
                    success: response.data.success
                };

                localStorage.setItem("user", JSON.stringify(userData));

                // Also store the token separately if needed for API calls
                localStorage.setItem("token", response.data.jwtToken);

                navigate('/dashboard');
                console.log("Login response:", response.data);
            }
        } catch (err) {
            console.error('Login error:', err);
            if (err.response?.data?.message) {
                alert(err.response.data.message);
            } else if (err.response?.data?.error) {
                alert(err.response.data.error);
            } else {
                alert('Login failed');
            }
        }
    };

    const handleForgotPassword = () => {
        alert('Password reset functionality would be implemented here!');
    };

    return (
        <div className="min-h-screen w-full flex flex-col lg:flex-row">
            <div className="w-full lg:w-1/2 flex flex-col">
                <div className="flex justify-between items-center p-6 lg:px-24 lg:py-12">
                   <a href="/"> <div className="flex items-center">
                        <div className="w-8 h-8 bg-[#ff6900] rounded-full flex items-center justify-center">
                            <span className="text-white font-bold text-sm">L</span>
                        </div>
                        <span className="ml-2 font-semibold text-gray-800">Logo</span>
                    </div></a>
                    <a href="/register">
                        <button className="px-6 py-2 border border-[#ff6900] text-[#ff6900] rounded-lg hover:bg-[#ff6900] hover:text-white transition-colors duration-300">
                            Sign Up
                        </button>
                    </a>
                </div>

                <div className="flex-1 px-6 lg:px-24 pb-8">
                    <div className="max-w-md">
                        <h4 className="text-sm text-gray-600 mb-2">Welcome back!</h4>
                        <h1 className="text-2xl lg:text-3xl font-bold text-gray-900 mb-8 pacifico-font">Please Sign In</h1>

                        <form className="space-y-6" onSubmit={submitData}>
                            <div>
                                <label htmlFor="email" className="block text-sm font-medium text-gray-700 mb-2">
                                    Email address
                                </label>
                                <input
                                    type="email"
                                    id="email"
                                    value={formData.email}
                                    onChange={handleInputChange}
                                    placeholder="Enter email address"
                                    required
                                    className="w-full h-12 px-4 border border-gray-300 rounded-xl focus:ring-2 focus:ring-[#ff6900] focus:border-transparent outline-none transition-all"
                                />
                            </div>

                            <div>
                                <label htmlFor="password" className="block text-sm font-medium text-gray-700 mb-2">
                                    Password
                                </label>
                                <input
                                    type="password"
                                    id="password"
                                    value={formData.password}
                                    onChange={handleInputChange}
                                    placeholder="Enter password"
                                    required
                                    className="w-full h-12 px-4 border border-gray-300 rounded-xl focus:ring-2 focus:ring-[#ff6900] focus:border-transparent outline-none transition-all"
                                />
                            </div>

                            <div className="flex justify-between items-center">
                                <div className="flex items-center">
                                    <input
                                        type="checkbox"
                                        id="rememberMe"
                                        checked={formData.rememberMe}
                                        onChange={handleInputChange}
                                        className="w-4 h-4 text-cyan-500 border-gray-300 rounded focus:ring-cyan-500 focus:ring-2"
                                    />
                                    <label htmlFor="rememberMe" className="ml-2 text-sm text-gray-600">
                                        Remember me
                                    </label>
                                </div>
                                <button
                                    type="button"
                                    onClick={handleForgotPassword}
                                    className="text-sm text-[#ff6900] hover:text-[grey] transition-colors"
                                >
                                    I forgot my password
                                </button>
                            </div>

                            <button
                                type="submit"
                                className="w-full h-12 bg-[#ff6900] text-white rounded-xl font-medium hover:from-white hover:to-white hover:text-[white] hover:border hover:border-[#ffaa00] transition-all duration-500 transform hover:scale-105"
                            >
                                Sign In
                            </button>
                        </form>

                        {/* <div className="mt-8 p-4 bg-[#ffe4bc] border-blue-200 rounded-lg">
                            <p className="text-blue-800 text-sm font-medium mb-2">Demo Credentials:</p>
                            <p className="text-blue-700 text-xs">Email: user@example.com</p>
                            <p className="text-blue-700 text-xs">Password: password123</p>
                        </div> */}
                    </div>
                </div>
            </div>

            <div className="w-full lg:w-1/2  lg:min-h-screen">
                <img src="/img/logReg1.jpg" alt="" className='object-cover h-[600px] w-full' />
                {/* <div className="absolute inset-0 flex items-center justify-center p-8">
                    <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-8 text-center max-w-md">
                        <div className="w-24 h-24 bg-white/20 rounded-full mx-auto mb-6 flex items-center justify-center">
                            <svg className="w-12 h-12 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.031 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                            </svg>
                        </div>
                        <h3 className="text-white text-xl font-semibold mb-2">Secure Login</h3>
                        <p className="text-white/80 text-sm">
                            Your data is protected with enterprise-grade security. Sign in safely and access your personalized dashboard.
                        </p>
                    </div>
                </div>
                <div className="absolute top-16 right-16 w-16 h-16 bg-white/10 rounded-full animate-pulse"></div>
                <div className="absolute bottom-24 left-12 w-24 h-24 bg-white/5 rounded-full animate-pulse delay-1000"></div>
                <div className="absolute top-1/3 right-24 w-8 h-8 bg-white/20 rounded-full animate-pulse delay-500"></div> */}
                {/* <div className="absolute inset-0 overflow-hidden">
                    <div className="absolute top-1/4 left-1/4 w-2 h-2 bg-white/30 rounded-full animate-bounce"></div>
                    <div className="absolute top-3/4 right-1/3 w-1 h-1 bg-white/20 rounded-full animate-bounce delay-700"></div>
                </div> */}
            </div>
        </div>
    );
};

export default LoginForm;




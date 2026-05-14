import React, { useState } from 'react';

export default function LandingPage() {
  const [images, setImages] = useState([]);
  const [videos, setVideos] = useState([]);
  const [affiliateLink, setAffiliateLink] = useState('');
  const [title, setTitle] = useState('USA Online Opportunity');
  const [description, setDescription] = useState('Start promoting your USA CPA offers today.');

  const handleImages = (e) => {
    const files = Array.from(e.target.files);
    setImages(files.map((file) => URL.createObjectURL(file)));
  };

  const handleVideos = (e) => {
    const files = Array.from(e.target.files);
    setVideos(files.map((file) => URL.createObjectURL(file)));
  };

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <div className="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-6">

        {/* Admin Panel */}
        <div className="bg-white rounded-3xl shadow-2xl p-6 h-fit">
          <h2 className="text-3xl font-bold mb-6 text-center">
            Admin Panel
          </h2>

          <div className="mb-5">
            <label className="block mb-2 font-semibold">Landing Page Title</label>
            <input
              type="text"
              value={title}
              onChange={(e) => setTitle(e.target.value)}
              className="w-full border rounded-2xl p-3"
            />
          </div>

          <div className="mb-5">
            <label className="block mb-2 font-semibold">Description</label>
            <textarea
              value={description}
              onChange={(e) => setDescription(e.target.value)}
              className="w-full border rounded-2xl p-3 h-28"
            />
          </div>

          <div className="mb-5">
            <label className="block mb-2 font-semibold">Affiliate / CPA Link</label>
            <input
              type="text"
              value={affiliateLink}
              onChange={(e) => setAffiliateLink(e.target.value)}
              placeholder="https://your-link.com"
              className="w-full border rounded-2xl p-3"
            />
          </div>

          <div className="mb-5">
            <label className="block mb-2 font-semibold">Upload Images</label>
            <input
              type="file"
              accept="image/*"
              multiple
              onChange={handleImages}
              className="w-full border rounded-2xl p-3"
            />
          </div>

          <div className="mb-5">
            <label className="block mb-2 font-semibold">Upload Videos</label>
            <input
              type="file"
              accept="video/*"
              multiple
              onChange={handleVideos}
              className="w-full border rounded-2xl p-3"
            />
          </div>

          <button className="w-full bg-blue-600 hover:bg-blue-700 text-white rounded-2xl py-4 text-lg font-semibold transition-all">
            Save Landing Page
          </button>
        </div>

        {/* Landing Page Preview */}
        <div className="lg:col-span-2 bg-white rounded-3xl shadow-2xl overflow-hidden">
          <div className="bg-gradient-to-r from-blue-600 to-indigo-700 text-white p-10 text-center">
            <h1 className="text-5xl font-bold mb-4">{title}</h1>
            <p className="text-lg opacity-90">{description}</p>

            {affiliateLink && (
              <a
                href={affiliateLink}
                target="_blank"
                rel="noopener noreferrer"
                className="inline-block mt-6 bg-white text-blue-700 px-8 py-4 rounded-2xl text-lg font-bold hover:scale-105 transition-all"
              >
                Continue Now
              </a>
            )}
          </div>

          {/* Images */}
          <div className="p-8">
            <h2 className="text-3xl font-bold mb-6">Uploaded Images</h2>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              {images.length > 0 ? (
                images.map((img, index) => (
                  <img
                    key={index}
                    src={img}
                    alt="uploaded"
                    className="rounded-2xl shadow-lg w-full h-64 object-cover"
                  />
                ))
              ) : (
                <div className="bg-gray-200 rounded-2xl h-64 flex items-center justify-center text-gray-500">
                  No Images Uploaded
                </div>
              )}
            </div>
          </div>

          {/* Videos */}
          <div className="p-8 pt-0">
            <h2 className="text-3xl font-bold mb-6">Uploaded Videos</h2>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              {videos.length > 0 ? (
                videos.map((video, index) => (
                  <video
                    key={index}
                    src={video}
                    controls
                    className="rounded-2xl shadow-lg w-full h-64 object-cover"
                  />
                ))
              ) : (
                <div className="bg-gray-200 rounded-2xl h-64 flex items-center justify-center text-gray-500">
                  No Videos Uploaded
                </div>
              )}
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}
